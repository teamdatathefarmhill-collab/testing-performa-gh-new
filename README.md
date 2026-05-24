# Dashboard Performa Greenhouse — The Farmhill

Redesign dari `dashboard-performa-gh` dengan struktur yang dirombak:
- Sidebar nav 3 modul flat (Performa · Panen Harian · Evaluasi) + Weekly Report
- Hero KPI hierarkis (% Tercapai vs Est sebagai headline)
- AI Briefing prominent
- Riwayat & Kualitas Panen per GH (14 kolom lengkap)
- Standar Acuan card
- Weekly Report print-ready (A4) per GH
- Auto-popup H+1 panen (Senin/Kamis setelah panen Min/Rab)

## Deploy

### Opsi 1 — Single file (rekomendasi)
File `index.html` di folder ini sudah self-contained. Upload langsung ke:
- Vercel (drag-drop folder atau `vercel deploy`)
- Netlify
- GitHub Pages
- Cloudflare Pages
- Hosting statis apa pun

Tidak perlu build step, tidak perlu node_modules.

### Opsi 2 — Vercel CLI
```bash
cd deploy
vercel deploy --prod
```

## Tweaks (in-app)
- Density: Roomy / Compact
- Dark mode
- Accent palette: Brand / Forest / Olive
- Demo: Auto-popup H+1 (toggle untuk testing tanpa nunggu Senin/Kamis)

## Catatan migrasi ke data real
File ini saat ini pakai **mock data** (`GH_DATA` array di app.jsx).
Untuk wiring ke Google Sheets:
1. Port fungsi `loadData()` dari script lama ke single file ini
2. Replace `GH_DATA` constant dengan fetched data
3. Map field nama:
   - `populasi` → `popAwal`
   - `klas` → `lokasi`
   - dst sesuai schema di mock data

## File source

| File | Keterangan |
|------|------------|
| `index.html` | Bundled single-file (untuk deploy) |
| `../Dashboard Performa GH.html` | Source HTML shell (untuk edit) |
| `../app.jsx` | React components + mock data |
| `../tweaks-panel.jsx` | Tweaks panel helper |

Untuk edit, ubah file source lalu re-bundle.
