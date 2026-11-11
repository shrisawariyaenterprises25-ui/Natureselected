# Nature Selected: online store

A fast, static ecommerce site (plain HTML, CSS and JavaScript, no build step) for Nature Selected, a brand by Shri Sawariya Enterprises.

## Files

- `index.html`: the whole site (products, cart, WhatsApp checkout)
- `images/`: pouch photos and logo
- `.nojekyll`, `robots.txt`: hosting helpers

## Edit your products

Open `index.html` and find the `var P=[` list near the bottom. Each product looks like this:

```js
{id:"chia",n:"Chia Seeds",w:"200 g",p:249,c:"#9b30c8",g:"Seeds",img:"images/chia-seeds.webp",d:"Short description",nu:"Nutrition summary"}
```

- `p` is the price in rupees and `c` is the accent colour.
- `g` is the category (`Seeds` or `Powders`).
- Entries with no `id` show as "Coming soon". To launch one, give it `id`, `p`, `img`, `d` and `nu`, and put its photo in `images/`.
- Change the WhatsApp number at the top of the script: `var WA="919876543210";` (country code + number, no + or spaces).

## Put it on GitHub

1. Create a GitHub account and a **new repository** (for example `nature-selected`), public.
2. Upload everything in this folder to the repository root, with `index.html` at the top level. On the repository page choose **Add file > Upload files**, or use git:
   ```bash
   git init
   git add .
   git commit -m "Nature Selected website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/nature-selected.git
   git push -u origin main
   ```
3. Go to **Settings > Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`, then Save.
4. After a minute the site is live at `https://YOUR-USERNAME.github.io/nature-selected/`.

## Connect your GoDaddy domain

Replace `yourdomain.com` below with your domain.

**A. Add DNS records in GoDaddy** (My Products > your domain > DNS):

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR-USERNAME.github.io |

Optional IPv6 (AAAA records, name @): `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`.

- Delete any existing `A` record for `@` that GoDaddy added (the "parked" one) and the default `www` CNAME, so only the records above remain.
- The CNAME value is just `YOUR-USERNAME.github.io`, without the repository name.
- Don't use wildcard (`*`) records.

**B. Tell GitHub the domain.** In the repository go to **Settings > Pages > Custom domain**, enter `www.yourdomain.com` (or `yourdomain.com`) and Save. GitHub adds a `CNAME` file to your repo. Whichever you enter, the other one redirects to it automatically.

**C. Turn on HTTPS.** When the DNS check passes, tick **Enforce HTTPS**. The certificate can take from a few minutes up to an hour or more.

DNS changes can take from a few minutes to 24 hours to spread. Test with `dig yourdomain.com +noall +answer`, which should list the four 185.199.x.153 addresses.

## Before you go live

- Replace the placeholder prices (Mix Rs 299, Sunflower Rs 199, Chia Rs 249, Neem Rs 149).
- Confirm the phone number, email and FSSAI number in the footer and `index.html`.
- Checkout currently sends the order to WhatsApp. For online payments, move to a platform with a payment gateway (Shopify, WooCommerce) or add a payment-link service.
