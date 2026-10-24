# Google SERP API Pricing: What 1,000 Searches Actually Cost, and How ScraperAPI's Plans Stack Up

Most Google SERP API pricing pages quote numbers you can't compare. One vendor sells searches, another sells credits, a third sells API calls — and a "$49/month" plan can mean 49,000 Google searches at one company and about 4,000 at another. The gap between the advertised price and the real price usually hides in the credit multiplier.

Here's the short version. Google has no official SERP API (the Custom Search JSON API returns a custom index, not real organic results, and is being deprecated), so you're choosing between third-party providers in three buckets: SERP-only APIs like SerpApi that charge per search, budget providers like Serper, and general-purpose scraping platforms like ScraperAPI that bill everything through one credit pool. If you only ever need Google SERP data at a steady volume, the per-search providers are simpler and often cheaper. If Google is one of several targets in the same pipeline — or you want proxy rotation, JS rendering, and CAPTCHA handling from the same account — ScraperAPI's credit system is worth understanding, because its effective per-search price drops fast as you scale.

> **Quick take:** On ScraperAPI, one Google SERP request costs **25 credits**, not 1. The Business plan ($299/month, 3M credits) works out to roughly **$2.49 per 1,000 Google searches**, well below SerpApi's $25/1K entry rate. A 7-day trial with 5,000 credits costs nothing and needs no credit card. 👉 [Check ScraperAPI's current plans and start a free trial](https://www.scraperapi.com/pricing?fp_ref=coupons)

## Why the headline price lies: the 25-credit rule

ScraperAPI doesn't bill per search. It bills per credit, and credit cost depends on what you're requesting:

| Request type | Credits per request |
| --- | --- |
| Standard web page | 1 |
| Amazon / Walmart / eBay | 5 |
| Google & Bing (all subdomains) | 25 |
| LinkedIn | 30 |
| Sites behind Cloudflare, Datadome, or PerimeterX | +10 when bypassed |

That 25-credit figure comes straight from ScraperAPI's documentation: "A standard web request costs 1 credit. A Google SERP request costs 25 credits." The premium covers what Google actually requires — rotating residential and mobile IPs, anti-bot detection, CAPTCHA solving, and structured JSON parsing of the results.

The practical consequence: divide any plan's credit allowance by 25 and you get the real Google search count. The "$49 plan with 100,000 credits" is about 4,000 Google searches per month. That's the number to compare against per-search vendors — and it's the number most plan tables skip entirely.

One helpful tool here: ScraperAPI's dashboard includes a Domain Cost Estimator that shows the exact credit cost of any URL before you scrape it, and you can set a `max_cost` per request so a single heavy scrape can't drain your balance.

## ScraperAPI's full plan table

All seven tiers currently listed on the pricing page, with monthly and annual (billed annually) prices:

| Plan | Monthly / Annual price | Credits | ≈ Google SERP requests | Concurrency | Get it |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 / $44.10 | 100,000 | ~4,000/mo | 20 threads | [ Start with Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 / $134.10 | 1,000,000 | ~40,000/mo | 50 threads | [ Start with Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 / $269.10 | 3,000,000 | ~120,000/mo | 100 threads | [ Start with Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling (most popular) | $475 / $427.50 | 5,000,000 | ~200,000/mo | 200 threads | [ Start with Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 / $877.50 | 10,500,000 | ~420,000/mo | 300 threads | [ Start with Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 / $1,777.50 | 21,500,000 | ~860,000/mo | 500 threads | [ Start with Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | 22M+ | Custom | 500+ threads | [ Contact sales for Enterprise](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Annual billing takes 10% off every tier, so a year of Business costs $269.10/month instead of $299 — $3,229 vs $3,588 over twelve months. Every plan includes the same core feature set: JS rendering, premium residential and mobile proxies, automatic JSON parsing, rotating proxy pools, custom headers and sessions, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Features don't gate plans on ScraperAPI; volume and concurrency do.

## What a Google search actually costs on each plan

Divide credits by 25 and divide again by the price, and the effective cost per 1,000 Google searches looks like this:

| Plan | Effective cost per 1,000 searches |
| --- | --- |
| Hobby | ~$12.25 |
| Startup | ~$3.73 |
| Business | ~$2.49 |
| Scaling | ~$2.38 |
| Professional | ~$2.32 |
| Advanced | ~$2.30 |

Two things stand out. First, Hobby is expensive per search — that tier exists for light mixed scraping, and using it for Google SERP at any volume is poor value. Second, the curve flattens hard above Business. Moving from Business ($2.49/1K) to Advanced ($2.30/1K) saves about 8% per search while costing five times more per month. At Business and above, ScraperAPI's effective Google SERP rate sits in the $2–$2.50 range — mid-tier by market standards, far below SerpApi's entry pricing but above budget players like Serper.

The jump from Hobby to Startup is where the money is: 40,000 searches for $149 versus 4,000 for $49. If your monthly Google volume is above roughly 4,000, Hobby is the wrong tier regardless of budget.

## The limits that don't appear in the headline numbers

Three restrictions live in the docs rather than the pricing page, and each one can disqualify a plan:

- **Geotargeting is US & EU only on Hobby and Startup.** Country-level targeting anywhere else in the world requires Business ($299) or higher. If your SERP data needs German, Japanese, or Brazilian local results, the two cheapest plans won't do it.
- **Analytics history is 30 days on Hobby and Startup**, unlimited from Business up. Minor for most, relevant if you audit usage patterns over quarters.
- **Pay-as-you-go overage is only available on Scaling and above.** On Hobby through Business, when credits run out, scraping pauses until renewal unless you enable auto-upgrade (which moves you to the next tier, opt-in). On Scaling, Professional, Advanced, and Enterprise, you can keep going at a fixed per-credit rate with a monthly spending cap you set yourself.

That last one matters more than it sounds. If your search volume spikes mid-month — a client campaign, a seasonal crawl — a Business plan simply stops at the limit, while Scaling keeps running predictably. If mid-month overage protection is important to you, Scaling is effectively the entry point, not Business. 👉 [See ScraperAPI's Scaling plan and current annual pricing](https://www.scraperapi.com/pricing?fp_ref=coupons)

## How ScraperAPI compares to per-search SERP APIs

At a benchmark of 100,000 Google searches per month on month-to-month billing, here's how the verified public prices line up:

| Provider | Billing model | Cheapest route at 100K/mo | Per 1,000 searches | Notable terms |
| --- | --- | --- | --- | --- |
| ScraperAPI | Credits (25/Google request) | Business plan | ~$2.49 | Credits shared across all target types |
| SerpApi | Per search | Searcher plan | $7.25 | Only successful searches billed; unused searches don't roll over |
| Serper | Prepaid credits | Standard | $0.75–$1.00 | Entry pack $50; advertised $0.30/1K requires a 12.5M-credit pack; credits expire after 6 months |
| DataForSEO | Per batch | Standard Queue | $0.60 | Queue mode can take up to 45 minutes; faster modes cost more |
| Serply | Prepaid credits | Growth | $0.98 | Credits never expire; $49 upfront |
| Zenserp | Per search | Medium | $1.50 | — |
| ScrapingBee / HasData | Credits / per request | Startup / Business | $0.99 | — |

A few honest notes on this table. Litescrape, the comparison site that published this ranking, lists its own prepaid rate at $0.15/1K as the cheapest option — treat vendor-owned benchmarks accordingly. Serper's $0.30 figure gets quoted a lot; it's real, but it requires a 12.5-million-credit pack, which puts it out of reach for most readers searching "google serp api pricing" in the first place.

Where does that leave ScraperAPI? Its effective ~$2.49/1K at Business isn't the cheapest Google-only rate on the market, and pretending otherwise would be wrong. What you're buying for the difference is scope: the same credits cover Amazon (5/request), regular web pages (1/request), LinkedIn (30/request), and protected sites, with rendering and CAPTCHA handling bundled. Two scenarios make the math work:

1. **Mixed-target pipelines.** If half your credits go to Google and half to product pages or other sites, per-search SERP subscriptions don't cover the rest, and you'd be paying two vendors.
2. **Anti-bot headaches.** If Google's blocking has burned you on self-managed proxies, the 25-credit price already includes the proxy and CAPTCHA layer, so there's no separate proxy bill to compare.

If your workload is 100% Google SERP, steady volume, and you never touch rendering or CAPTCHAs elsewhere, a per-search provider at $0.60–$1.00/1K is genuinely the better deal. That's not a knock on ScraperAPI; it's just what the credit system is and isn't for.

## What happens when credits run out (and other billing details)

ScraperAPI bills by monthly request count, not bandwidth, and doesn't sell individual IPs from its pool. When you hit 100% of credits before renewal:

- Monthly plans (Student, Hobby, Startup, Business, Scaling, Professional): scraping pauses by default, or you turn on **auto-upgrade** to move to the next tier automatically — which usually means a better price per credit. You can also contact support for a custom plan.
- Professional and Advanced monthly plans include **Pay-As-You-Go** by default; a pop-up offers extra credits at a fixed rate when you hit the cap.
- Annual plans can renew early to get a fresh batch of credits.
- Enterprise accounts can continue at a fixed per-credit rate mid-cycle.

Cancellation is from the dashboard anytime, with no charge for cancelling.

## Free trial and refund terms

The trial terms are unusually clean. You get 1,000 free API credits per month on the free plan (max 5 concurrent connections) for as long as you keep the account, plus 5,000 free requests during your first 7 days for larger-scale testing — no credit card required at signup. If the paid service doesn't work out, ScraperAPI's policy is a 7-day, no-questions-asked refund handled through support.

That combination makes the trial low-risk in a practical sense: you can validate your Google parsing results on free credits before any payment, and the refund window covers the first billing period after you commit. 👉 [Try ScraperAPI free for 7 days — no credit card needed](https://www.scraperapi.com/pricing?fp_ref=coupons)

## FAQ

**How many Google searches do I get on ScraperAPI's $49 plan?**
About 4,000 per month. Hobby includes 100,000 credits and each Google or Bing request costs 25 of them. The same math applies to every tier: divide credits by 25.

**Does the 25-credit rate include rendering and CAPTCHA solving for Google?**
Yes. The 25-credit cost covers Google's anti-bot detection, proxy rotation, CAPTCHA handling, and structured JSON output for the SERP request. The separate premium/rendering multipliers apply to regular web scraping, not to the built-in Google endpoint pricing.

**What's the cheapest ScraperAPI plan for global (non-US/EU) geotargeting?**
Business at $299/month. Hobby and Startup are limited to US and EU locations.

**Do unused ScraperAPI credits roll over?**
Monthly credits reset at renewal. On annual plans, you can renew early for a fresh batch. There's no indefinite rollover pool, unlike prepaid-credit competitors such as Serply, whose credits never expire.

**Is there a truly free SERP API from Google?**
Google's Custom Search JSON API allows 100 free queries per day, but it returns results from a custom index rather than the organic SERP, and Google has signaled it will be deprecated. That's why third-party SERP APIs exist at all.

## Which plan should you pick?

Match the plan to your actual monthly Google volume and target mix:

- **Under ~4,000 Google searches/month, plus some light scraping:** Hobby ($49) covers it, but honestly, start with the free 1,000 monthly credits and see how far they stretch first.
- **40,000–120,000 Google searches or mixed targets with country-level geo:** Business ($299/month, ~$2.49/1K) is the sensible floor. It's also where global geotargeting and unlimited analytics kick in.
- **Spiky volume or no tolerance for mid-month stoppages:** Scaling ($475) and up, for pay-as-you-go overage at a fixed rate with a spending cap.
- **Pure Google SERP, predictable volume, no other targets:** ScraperAPI's credit pool works against you here. A per-search provider like Serper ($0.75–$1.00/1K) or DataForSEO's queue mode ($0.60/1K, slow) will cost less — SerpApi at $7.25–$25/1K is priced for its data depth, not its rate.

Two checks before you commit: run your monthly volume through the credits ÷ 25 math so you know which tier actually fits, and confirm your target countries — if any fall outside the US and EU, Hobby and Startup are off the table before price even enters the discussion. Then take the 7-day trial for a spin; if it doesn't parse what you need, the refund window has you covered. 👉 [Start your ScraperAPI trial and compare all plan prices](https://www.scraperapi.com/pricing?fp_ref=coupons)
