# 🚀 Airdrop Tracker — Anime-Themed Crypto Dashboard

## Deskripsi
Dashboard sederhana untuk mengelola dan mengingatkan airdrop crypto dengan tema anime (warna pastel, ilustrasi karakter anime).

## Fitur Utama
- ✅ Tambah, Edit, Hapus entry airdrop (CRUD)
- ⏰ Setiap entry: Nama Airdrop, Deadline, Status, Notes, URL Link
- 🔔 Reminder: tampilkan airdrop dengan deadline < 3 hari
- 🔍 Search & filter berdasarkan nama/status
- 🎨 Tema anime dengan warna pastel

## Status Airdrop
- `belum_klaim` — Belum diklaim
- `sudah_klaim` — Sudah diklaim
- `pending` — Menunggu

## API Endpoints (RESTful)
| Method | Endpoint           | Description          |
|--------|--------------------|----------------------|
| GET    | /api/airdrops      | Ambil semua airdrop  |
| POST   | /api/airdrops      | Tambah airdrop baru  |
| GET    | /api/airdrops/[id] | Ambil satu airdrop   |
| PUT    | /api/airdrops/[id] | Update airdrop       |
| DELETE | /api/airdrops/[id] | Hapus airdrop        |
| POST   | /api/seed          | Seed dummy data      |

## Tech Stack
- **Framework**: Next.js 16 + App Router
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4 + shadcn/ui
- **Database**: Prisma ORM + SQLite
- **Icons**: Lucide React
- **Animations**: CSS (sparkle, float, pulse)
- **Images**: AI-generated anime illustrations

## Cara Menjalankan
```bash
# Install dependencies
bun install

# Setup database
bun run db:push
bun run db:generate

# Jalankan development server
bun run dev
```

## Struktur File Penting
```
src/
├── app/
│   ├── page.tsx              ← Dashboard UI (anime theme)
│   ├── layout.tsx            ← Root layout
│   ├── globals.css           ← Anime pastel theme styles
│   └── api/
│       ├── airdrops/
│       │   ├── route.ts      ← GET (list), POST (create)
│       │   └── [id]/route.ts ← GET, PUT, DELETE
│       └── seed/route.ts     ← Seed dummy data
├── lib/
│   └── db.ts                 ← Prisma client
prisma/
└── schema.prisma             ← Airdrop model
public/
├── anime-hero.png            ← Anime illustration
├── anime-mascot.png          ← Anime mascot
└── anime-reminder.png        ← Anime reminder illustration
```

## Database Schema (Prisma)
```prisma
model Airdrop {
  id        String   @id @default(cuid())
  name      String
  deadline  DateTime
  status    String   @default("belum_klaim")
  notes     String   @default("")
  url       String   @default("")
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

---
Made with ✨ anime vibes
