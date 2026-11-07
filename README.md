# Hasmi Consultancy — website

A responsive Next.js 16 static website for Hasmi Consultancy, Mumbai, Maharashtra. It is configured for classic Firebase Hosting using Next.js static export.

## Included

- Home, About, Services, SEO, Social Media, Advertising, Website Development, Portfolio, Contact, Privacy Policy and Terms pages.
- Responsive blue-and-white corporate styling.
- WhatsApp contact links and enquiry form. The form opens WhatsApp with a pre-filled message; this starter does not store form submissions.
- Basic metadata, robots.txt and sitemap.xml placeholders.
- Firebase Hosting configuration for the generated `out/` directory.

## Requirements

- Node.js 20.9 or later (use a current supported LTS release)
- npm
- A Google account and Firebase project

## 1. Install and run locally

```bash
npm install
npm run dev
```

Open http://localhost:3000.

## 2. Build the static website

```bash
npm run build
```

Next.js exports the website into `out/`. Confirm `out/index.html` exists.

## 3. Firebase project and CLI

1. Create a project at https://console.firebase.google.com/ (for example, `hasmi-consultancy`).
2. Install the Firebase CLI:

```bash
npm install -g firebase-tools
firebase login
```

3. This project already includes `firebase.json` configured to publish the Next.js `out/` folder. Link it to your Firebase project without reinitialising or overwriting that configuration:

```bash
firebase use --add
```

Select your existing Firebase project and assign the alias `default`. This creates `.firebaserc`. Alternatively, copy `.firebaserc.example` to `.firebaserc` and replace the placeholder with your exact Firebase project ID.

4. Build and deploy:

```bash
npm run build
firebase deploy --only hosting
```

Firebase will show the live `web.app` and `firebaseapp.com` URLs in the deployment output.

## 4. Before publishing

Edit `src/lib.ts`:

- Confirm the WhatsApp number in international format without `+` or spaces. It is currently `917738600954`.
- Replace `hello@yourdomain.com` with a real business email address once available.

Edit `src/app/contact/page.tsx`, `src/components/Site.tsx`, and the legal pages if you add a phone number, email, office address or other business details.

Replace `YOUR-DOMAIN.example` in `public/robots.txt` and `public/sitemap.xml` with the final live domain. Update `metadataBase` in `src/app/layout.tsx` to the live canonical origin after you know it.

Review the privacy policy and terms against your actual business processes. The provided text is a starter, not legal advice. The portfolio intentionally uses illustrative service concepts and does not claim fabricated client results.

## 5. Connect a custom domain later

In Firebase Console → Hosting → Add custom domain, enter the domain you purchase. Copy the exact DNS records Firebase gives you into your registrar's DNS panel. Wait for verification and SSL provisioning. Do not guess DNS values.

## Contact form behaviour

Because this version is exported as a static website, the form opens WhatsApp with the visitor's details pre-filled. The visitor must press Send in WhatsApp. The site does not silently send or save enquiries. To save leads in a database later, connect Firestore with security rules or add a trusted server-side form endpoint.

## Static hosting note

This project uses `output: 'export'`. It does not use Next.js server actions, API routes, middleware, server-side rendering at request time or other features that require a Next.js server. For a full-stack Next.js site, consider Firebase App Hosting instead of classic static Hosting.
