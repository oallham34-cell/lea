# LEA — MAKEUP & PERFUMES

Full-stack Arabic RTL beauty-store catalog and WhatsApp ordering website.

## Stack

- Next.js App Router
- TypeScript
- Prisma
- PostgreSQL
- JWT-based httpOnly admin session
- bcrypt password hashing
- Zod validation
- Local browser cart + favorites
- WhatsApp order generation
- Responsive RTL UI

## Setup

```bash
cp .env.example .env
npm install
npx prisma generate
npm run db:push
npm run db:seed
npm run dev
```

Open `http://localhost:3000`.

## Production checklist

- Replace every `REPLACE_WITH_*` store value.
- Generate a strong `AUTH_SECRET` (32+ random characters).
- Use a managed PostgreSQL database.
- Image upload is implemented at `/api/admin/upload` and stores files under `public/uploads` for a traditional persistent server. For serverless deployment, replace this adapter with persistent/object storage (S3/R2/Supabase Storage/etc.).
- Put the site behind HTTPS.
- Configure backups and monitoring.
- Replace demo products with real LEA inventory.
- Add rate limiting/WAF to admin login and admin APIs.
- If deploying serverless, use an upload API + object storage rather than writing to the application filesystem.

## Admin

`/admin/login`

Credentials come from `ADMIN_EMAIL` and `ADMIN_PASSWORD` at seed time. Passwords are hashed with bcrypt.

## Important

There is intentionally no online payment and no customer account system. Orders are assembled client-side from the cart and opened as a single WhatsApp message to the configured store number.
