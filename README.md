# mpjp.pl — Anamnesis landing page

One static page shown while the app is being built. Plain HTML + CSS, no JavaScript,
no build step, no cookies, no third-party requests (fonts are self-hosted).

```
public/
  index.html    the landing page (hero, "Czym jest", contact)
  404.html      served by Netlify for unknown paths
  site.css      styles + @font-face (snapshot of the app's marketing-site stylesheet)
  fonts/        self-hosted Spectral, Hanken Grotesk, IBM Plex Mono
  favicon.svg
  _headers      CSP (script-src 'none'), HSTS, nosniff, no-referrer, frame DENY
  robots.txt, sitemap.xml
netlify.toml    publish = "public", no build command
```

Contact: `kontakt@mpjp.pl` (mailto links only — no form).

## Local preview

```bash
python3 -m http.server -d public 8000   # http://localhost:8000
```

## Deploy (Netlify)

1. Netlify → Add new site → Import from GitHub → this repo. Build settings come from `netlify.toml`.
2. Domain management → add `mpjp.pl` (and `www.mpjp.pl`), point DNS as Netlify instructs;
   HTTPS is issued automatically.
3. Check live headers: `curl -sI https://mpjp.pl/ | grep -i content-security-policy`.

Independent of the `therapist-copilot` monorepo: the hero is a one-time copy of its
`Web.dc.html` hero and is not kept in sync.
