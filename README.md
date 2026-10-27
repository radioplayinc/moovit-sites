# Moovit Sites — sales site (pay site)

The checkout that sells Bookit booking websites. Live at https://moovit-sites.pages.dev, repo `radioplayinc/moovit-sites`.

Same no-scroll, one-screen-at-a-time system as the booking template. Flow: loader → packages → funding (full vs 50% deposit) → care plan → company details → review → done. Payment opens the Jim link in a popup (new tab on mobile) — Jim blocks iframe framing, never iframe it.

## Offer (locked)

- Starter $2,499 (live up to 7 days), Pro $3,499 (up to 14 days, most movers pick this), Premium $3,999 (up to 30 days). Timelines run from the intake form coming back.
- 50% deposits: Starter $1,249, Pro $1,749, Premium $1,999. Balance only due when the site ships, and only once the buyer is happy.
- Care plans: Starter $70, Pro $150, Premium $200 per month, first month free, billed on the monthly maintenance invoice. Cancel anytime.
- Guarantee: "We fix it until you are happy, and you do not pay the final balance until you are."
- After payment: an intake form lands in the buyer's inbox (logo, service area, pricing). The build starts when it comes back.

## Editing

Everything editable lives in the `CONFIG` block at the top of the script in `index.html`: packages, Jim payment links, care plans, `demoUrl`. Duplicating for a vertical is a CONFIG swap — see `~/workspace/custom-skills/bookit-site/references/SALES_SITE.md`. Verify every Jim link opens its exact amount before delivery. Never ship with `PASTE_DEMO_URL`.

Title stays as-is on the movers sales site: "Basqi — Booking websites for moving companies". Sell as Moovit Sites; rename nothing.

## SEO pack

Ships since 2026-10-27. Spec: `~/workspace/custom-skills/bookit-site/references/SEO_PACK.md`.

- `index.html` head: title, meta description, canonical, OG/Twitter, JSON-LD `@graph` (`Service` + offer catalog + `FAQPage`, 8 Q&As), plus a `<noscript>` summary. The no-scroll checkout flow is untouched.
- `faq.html`: scrolling page with the same 8 FAQs in visible HTML.
- `sitemap.xml`, `robots.txt`, `llms.txt` at the root.
- FAQ answers must match verbatim in all 3 copies; prices in the schema must match `CONFIG` exactly. No phone or email is published on this site — none is in the JSON-LD either.
- After deploy (free): submit the sitemap in Google Search Console + Bing Webmaster Tools.

## Deploy

Push to `main` — Cloudflare Pages auto-deploys (preset None, no build command, output directory `/`). Text files go through the connected GitHub snapshot push; binary assets (`logo.jpg`) already live in the repo. Verify from production: fetch the live URL and confirm the title, prices, timelines, guarantee, and the exact Jim link amounts.
