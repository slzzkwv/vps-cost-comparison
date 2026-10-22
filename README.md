# Ubuntu virtual server hosting: what a China-route VPS actually costs and how to test one before the refund window closes

Ubuntu virtual server hosting is a commodity. A 1 vCPU / 4 GB Ubuntu box with root access costs single-digit dollars a month in 2026, and the operating system itself is free. So when a provider lists Ubuntu plans at $29 to $199 a month, the honest question is what the extra money is buying.

At GoMami Networks, it buys the network path to mainland China. Ubuntu is simply one of the OS templates you select: 22.04 LTS or 24.04 LTS when you order, with 20.04 LTS also available on the reinstall page. The product wrapped around that template is CN2 / AS9929 / CMIN2 routing, a vendor claim of under 50 ms RTT to mainland China, and AMD EPYC or Ryzen hardware underneath.

That reframes the decision. You are deciding whether a China-optimised route is worth four to six times what a generic Ubuntu VPS costs. Below is what each tier contains, which prices you should verify before paying, what the terms page says that the landing page doesn't, and how to benchmark the route inside the 24-hour refund window without disqualifying yourself from it.

> **Quick pick:** if your users are in mainland China and you need one small always-on box, start with the Hong Kong Pulse line (from $39/month on the homepage listing, $59 on the store listing — confirm at checkout) and benchmark the route within the first 24 hours. If nobody in your audience is in China, a $5–$10 Ubuntu VPS is the better purchase; the premium here pays for routing quality. 👉 [Open GoMami's Hong Kong plan list](https://gomami.io/store/hkg-pulse?aff=415)

## What an Ubuntu instance from GoMami actually includes

You get a self-managed virtual server with root access and an Ubuntu image, deployed automatically in about 1–5 minutes after payment, with the IP address and login credentials arriving by email. Patching, hardening, and backups are yours to handle.

The OS side is straightforward. At order time you choose from Ubuntu 22.04 LTS, 24.04 LTS, Debian 11/12, CentOS Stream 9, AlmaLinux 8/9, or Windows Server 2019/2022. The reinstall page offers a slightly wider list: Ubuntu 20.04, 22.04 and 24.04 LTS, Debian 11/12/13, CentOS 7 and Stream 9, AlmaLinux 9/10, Rocky Linux 8/9/10, Fedora 41/42. Anything outside those lists goes on through the Custom ISO feature, which can also mount network operating systems.

Management runs through a VirtFusion-based panel: power control, VNC console, rescue mode, reinstall, password reset, boot order, swap configuration, and traffic graphs. There's a RESTful API if you'd rather script provisioning than click.

A few practical details that catch people out. Swap changes only take effect after a reinstall, so configure swap the way you want it before you build anything on the box. If you install from a custom ISO, unmount it and restore the boot order afterwards, otherwise the server boots back into the installer instead of your new system. First login is standard `ssh root@your_server_ip`; accept the ED25519 fingerprint on first connect, then create a normal user and use `sudo` for privileged work rather than staying on root permanently.

👉 [Order an instance and pick Ubuntu 24.04 at checkout](https://bit.ly/Gomami)

## Hong Kong plans: every tier currently listed

Hong Kong is where most China-facing workloads land, and it carries four separate product lines. Pulse is EPYC 7763 and the cheapest option. Peak X5 runs Ryzen 9 9950X at up to 5.7 GHz, which matters for game servers and single-threaded database work. Turin is EPYC 9575F on Zen 5 with noticeably larger disks. Forge is a 56-core, 128 GB machine that sits closer to a dedicated server.

Prices below are list prices. Confirm the figure on the order page before you pay, for reasons explained after the table.

| Plan | Platform | vCPU / RAM / NVMe | Traffic (port) | List price | Order |
| --- | --- | --- | --- | --- | --- |
| HKG.Pulse.Nano | EPYC 7763 | 2 / 2 GB / 40 GB | 500 GB (1 Gbps) | $49/mo | [Order Pulse Nano](https://gomami.io/store/hkg-pulse?aff=415) |
| HKG.Pulse.Mini | EPYC 7763 | 2 / 4 GB / 60 GB | 1 TB (1 Gbps) | $59/mo | [Order Pulse Mini](https://gomami.io/store/hkg-pulse?aff=415) |
| HKG.Pulse.Air | EPYC 7763 | 4 / 8 GB / 80 GB | 2 TB (1 Gbps) | $119/mo | [Order Pulse Air](https://gomami.io/store/hkg-pulse?aff=415) |
| HKG.Pulse.Pro | EPYC 7763 | 8 / 16 GB / 100 GB | 5 TB (3 Gbps) | $269/mo | [Order Pulse Pro](https://gomami.io/store/hkg-pulse?aff=415) |
| HKG.Pulse.Ultra | EPYC 7763 | 12 / 32 GB / 300 GB | 10 TB (3 Gbps) | $499/mo | [Order Pulse Ultra](https://gomami.io/store/hkg-pulse?aff=415) |
| HKG.Peak.X5.Mini | Ryzen 9 9950X | 2 / 4 GB / 40 GB | 1 TB (2 Gbps) | $59/mo | [Order Peak X5 Mini](https://gomami.io/store/hkg-peak?aff=415) |
| HKG.Peak.X5.Air | Ryzen 9 9950X | 4 / 8 GB / 60 GB | 2 TB (2 Gbps) | $99/mo | [Order Peak X5 Air](https://gomami.io/store/hkg-peak?aff=415) |
| HKG.Peak.X5.Pro | Ryzen 9 9950X | 6 / 16 GB / 80 GB | 5 TB (5 Gbps) | $199/mo | [Order Peak X5 Pro](https://gomami.io/store/hkg-peak?aff=415) |
| HKG.Turin.Mini | EPYC 9575F | 2 / 4 GB / 100 GB | 1 TB (2 Gbps) | $69/mo | [Order Turin Mini](https://gomami.io/store/hkg-turin?aff=415) |
| HKG.Turin.Air | EPYC 9575F | 4 / 8 GB / 140 GB | 2 TB (2 Gbps) | $129/mo | [Order Turin Air](https://gomami.io/store/hkg-turin?aff=415) |
| HKG.Turin.Pro | EPYC 9575F | 6 / 16 GB / 180 GB | 5 TB (5 Gbps) | $299/mo | [Order Turin Pro](https://gomami.io/store/hkg-turin?aff=415) |
| HKG.Turin.Ultra | EPYC 9575F | 12 / 32 GB / 220 GB | 10 TB (5 Gbps) | $599/mo | [Order Turin Ultra](https://gomami.io/store/hkg-turin?aff=415) |
| HKG.Forge.Mini | EPYC 7663, 56C/112T | 128 GB / 960 GB | 10 TB (2 Gbps) | $599/mo | [Order Forge Mini](https://gomami.io/store/hkg-forge?aff=415) |
| HKG.Forge.Air | EPYC 7663, 56C/112T | 256 GB / 4 TB | 20 TB (2 Gbps) | $899/mo | [Order Forge Air](https://gomami.io/store/hkg-forge?aff=415) |

## Japan, Singapore and Los Angeles: every tier currently listed

These three regions run the Pulse line only. Los Angeles carries the largest traffic allowances and the widest spread of plans, up to a Titan tier with 30 TB and a 10 Gbps port.

| Plan | Platform | vCPU / RAM / NVMe | Traffic (port) | List price | Order |
| --- | --- | --- | --- | --- | --- |
| JPN.Pulse.Nano | EPYC | 2 / 2 GB / 40 GB | 500 GB (1 Gbps) | $29/mo | [Order JPN Nano](https://gomami.io/store/jpn-pulse?aff=415) |
| JPN.Pulse.Mini | EPYC | 2 / 4 GB / 60 GB | 1 TB (1.5 Gbps) | $49/mo | [Order JPN Mini](https://gomami.io/store/jpn-pulse?aff=415) |
| JPN.Pulse.Air | EPYC | 4 / 8 GB / 80 GB | 2 TB (1 Gbps) | $89/mo | [Order JPN Air](https://gomami.io/store/jpn-pulse?aff=415) |
| JPN.Pulse.Pro | EPYC | 8 / 16 GB / 100 GB | 5 TB (3 Gbps) | $169/mo | [Order JPN Pro](https://gomami.io/store/jpn-pulse?aff=415) |
| JPN.Pulse.Ultra | EPYC | 12 / 32 GB / 300 GB | 10 TB (3 Gbps) | $338/mo | [Order JPN Ultra](https://gomami.io/store/jpn-pulse?aff=415) |
| SIN.Pulse.Nano | EPYC | 2 / 2 GB / 40 GB | 500 GB (1 Gbps) | $29/mo | [Order SIN Nano](https://gomami.io/store/sin-pulse?aff=415) |
| SIN.Pulse.Mini | EPYC | 2 / 4 GB / 60 GB | 1 TB (1 Gbps) | $49/mo | [Order SIN Mini](https://gomami.io/store/sin-pulse?aff=415) |
| SIN.Pulse.Air | EPYC | 4 / 8 GB / 80 GB | 2 TB (1 Gbps) | $89/mo | [Order SIN Air](https://gomami.io/store/sin-pulse?aff=415) |
| SIN.Pulse.Pro | EPYC | 8 / 16 GB / 100 GB | 5 TB (3 Gbps) | $169/mo | [Order SIN Pro](https://gomami.io/store/sin-pulse?aff=415) |
| SIN.Pulse.Ultra | EPYC | 12 / 32 GB / 300 GB | 10 TB (3 Gbps) | $338/mo | [Order SIN Ultra](https://gomami.io/store/sin-pulse?aff=415) |
| LAX.Pulse.Nano | EPYC | 2 / 2 GB / 40 GB | 1 TB (1 Gbps) | $29/mo | [Order LAX Nano](https://gomami.io/store/lax-pulse?aff=415) |
| LAX.Pulse.Mini | EPYC | 2 / 4 GB / 60 GB | 2 TB (1 Gbps) | $59/mo | [Order LAX Mini](https://gomami.io/store/lax-pulse?aff=415) |
| LAX.Pulse.Air | EPYC | 4 / 8 GB / 80 GB | 4 TB (2 Gbps) | $129/mo | [Order LAX Air](https://gomami.io/store/lax-pulse?aff=415) |
| LAX.Pulse.Pro | EPYC | 6 / 16 GB / 100 GB | 8 TB (3 Gbps) | $259/mo | [Order LAX Pro](https://gomami.io/store/lax-pulse?aff=415) |
| LAX.Pulse.Ultra | EPYC | 12 / 32 GB / 300 GB | 15 TB (5 Gbps) | $599/mo | [Order LAX Ultra](https://gomami.io/store/lax-pulse?aff=415) |
| LAX.Pulse.Titan | EPYC | 12 / 32 GB / 600 GB | 30 TB (10 Gbps) | $999/mo | [Order LAX Titan](https://gomami.io/store/lax-pulse?aff=415) |

## Why you should confirm the price on the order page

GoMami currently circulates more than one price list for the same plans, and the contradictions are visible without digging. The clearest example is the Hong Kong Pulse line, where one listing shows a Nano at $49 and a Mini at $59, while the homepage shows an EPYC 7763 Mini at $39. A Mini listed cheaper than a Nano in the same series doesn't make sense, which tells you at least one of those sets isn't current. Treat every figure in the two tables above as a list price and read the number on the checkout screen.

The Turin line has the same problem in a milder form: a June 2026 lineup article and an independent stock tracker both show Air at $129 and Pro at $299, while a separate comparison piece lists $99 and $199. The tables use $129/$299 because two sources agree on it, and you should still verify.

Los Angeles is worth a specific caution. GoMami's official purchase documentation lists three locations: Hong Kong, Japan and Singapore. The LAX series exists as a store page with six plans and full specifications, and third-party coverage treats it as a launched region, but it doesn't appear in the documented location list. If LAX is central to your plan, confirm availability before building around it.

On discounts: the official checkout flow includes a Promo Code field where you enter a code before payment. Codes such as `GOMAMI365` circulate widely in third-party articles and Telegram channels, sometimes described as recurring and sometimes as annual-only. None of that is confirmed on GoMami's own pages, and the two descriptions contradict each other. Enter a code if you have one and check the order summary before completing payment; don't budget on a discount you haven't seen applied.

## The terms page matters more than the landing page

Four things on GoMami's own documentation change how you should plan, and none of them appear in the promotional write-ups.

**Backups are not included.** The Terms of Service state plainly that GoMami does not perform data backups for customer accounts and is not liable for data loss, and recommend that customers back up regularly. Several affiliate articles claim every plan ships with daily automated backups to S3. The terms win. Budget for your own backup target: object storage elsewhere, a second VPS, or `restic` to somewhere you trust.

**The 24-hour refund is conditional.** It covers first purchases, once per user. It's void if you use more than 10 GB of traffic within those 24 hours, pay in cryptocurrency, have your IP blackholed by a DDoS attack, or get terminated for a terms violation. Renewal orders and spent account credit don't qualify either. Processing fees from the original transaction are deducted from whatever comes back.

**Resizing means a support ticket.** The documentation states that plan changes currently require contacting support through the ticket system. There's no self-service upgrade button in the panel. Pick the tier you actually need at order time, or accept a support round-trip later.

**600 Gbps is a ceiling rather than a default.** The homepage advertises up to 600 Gbps of DDoS mitigation; the docs describe best-effort protection included by default with 600 Gbps advanced scrubbing as an optional extra. Plan as though you have baseline protection, and ask support if you need the higher tier.

## Is a $39 Ubuntu VPS worth it next to a $6 one?

Only if mainland China latency and evening-peak throughput are things your project measurably loses money on. For everyone else, a general-purpose host wins on price by a wide margin.

Hostinger's KVM 1 plan is advertised at $6.49/month on a promotional rate, renewing at $11.99/month on a two-year commitment, with 1 vCPU, 4 GB RAM, 50 GB NVMe and 4 TB of bandwidth. Vultr's high-performance AMD entry tier is around $6/month for 1 vCPU, 1 GB RAM, 25 GB NVMe and 2 TB. A GoMami Singapore or Japan Nano at $29/month works out to roughly $348 a year, about 4.5 times Hostinger's first-year figure. What you're buying with that gap is route quality, since the RAM and disk are comparable or worse.

The reason people pay it: standard 163 backbone paths into China congest badly during the 20:00–23:00 Beijing window, which is precisely when consumer traffic peaks. CN2, AS9929 and CMIN2 are the premium alternatives, and running all three across telecom, unicom and mobile is what "China Mainland Optimized Pro" refers to here.

Third-party evidence exists but is thin and worth reading carefully. A Lowendaff Blog test in early 2026 on GoMami's Turin infrastructure measured sustained throughput of about 2.16 Gbps to Singapore at roughly 40 ms, and 1.76 Gbps to Shenzhen Telecom with 893 Mbps on the return. One independent test on a Pulse EPYC 7763 instance running Debian 13 traced Singapore-to-Beijing paths on the optimised routes at 70–80 ms. Neither of those is a broad survey, and neither tested Ubuntu specifically, so treat them as single data points rather than guarantees. The sub-50 ms figure is the vendor's own claim.

Three groups should stop here and buy something cheaper: a personal blog with no Chinese readers, an internal tool used from one office in Europe, and anyone who expects the provider to handle patching and backups.

## How to use the 24-hour window without voiding it

Test small, test fast, and test at the right hour. The 10 GB cap is the trap: on a 1 Gbps port, a full-speed throughput run burns through 10 GB in about 80 seconds and disqualifies you from a refund before you've learned anything useful.

A workable sequence:

1. Ping and traceroute from your own machine and from a box in your users' city. Look for CN2 (AS4809), AS9929 or CMIN2 hops rather than a congested 163 path.
2. Run short throughput bursts. Cap iperf3 to a few seconds, or pull a single file of a few hundred megabytes.
3. Repeat the test between 20:00 and 23:00 Beijing time. A midday result tells you almost nothing about the problem you're solving.
4. Time an `apt update` and a package install. For Ubuntu specifically, repository reachability is part of the practical experience and almost nobody benchmarks it.
5. Stay under 10 GB total, then decide: keep the box or open a billing ticket.

👉 [Pick a Hong Kong plan to benchmark tonight](https://gomami.io/store/hkg-pulse?aff=415)

## Limits that matter after the first month

Traffic overage works differently by product. On VPS plans, bandwidth may be throttled once the monthly quota is used, with the exact policy depending on the plan, and quotas reset each billing cycle. Forge plans bill overage at $0.06/GB instead. No throttled speed is published, so size against your peak month rather than the average.

CPU falls under a fair-use expectation. Sustained load that affects other customers on the same node can result in performance throttling. Fine for build jobs and traffic spikes; not fine as a permanent pattern on the cheapest tier.

The terms also prohibit Tor, open proxies and anonymous proxy services, bots, spam, and resource abuse. If the plan was to use the box as a proxy node rather than a web or application server, that's a hard stop rather than a grey area.

Payment methods are credit card, Stripe Alipay and cryptocurrency, with account credit applicable to orders. Crypto payments are explicitly non-refundable, so pay by card if you intend to use the refund window.

## FAQ

**Is GoMami managed hosting?** No. Every plan is self-managed with root access, and administration of the server is your responsibility.

**Which Ubuntu versions can I install?** 22.04 and 24.04 LTS at order time; 20.04, 22.04 and 24.04 LTS from the reinstall page. Anything else goes through a custom ISO.

**Can I upgrade my plan later?** Yes, currently by opening a support ticket rather than through the panel.

**What happens if I exceed my monthly traffic?** On VPS plans the connection may be throttled until the next billing cycle. Forge plans bill overage at $0.06/GB.

**Is there an uptime SLA?** No SLA figure appears on the site, so treat availability as unguaranteed and architect accordingly.

**Can I add extra IPv4 addresses?** Forge listings show additional IPs at $10 each per month, capped at four per server. For VPS plans, ask support.

## Which plan to order

Match the tier to the workload rather than climbing the price ladder.

A small site, an API, or light automation with Chinese visitors fits HKG.Pulse.Mini: two cores and 4 GB handles WordPress, a small Docker stack, or a lightweight API, and 1 TB of traffic covers most brochure-scale sites. For a game server, a real-time API, or a database that lives on single-thread speed, HKG.Peak.X5.Mini is the reason the Ryzen line exists. Media-heavy sites and anything with large working sets justify HKG.Turin.Mini mainly for the 100 GB of NVMe on Zen 5. If your audience is in Southeast Asia rather than mainland China, SIN.Pulse.Nano at $29 covers it, and JPN.Pulse.Nano does the same for Japan-adjacent traffic.

Two things to check on the checkout screen before you pay: the actual price for the series you picked, since the homepage and the store pages disagree in places, and your billing cycle, since longer terms are cheaper but no discount percentage is published.

👉 [Start with HKG.Pulse.Mini from the Hong Kong plan list](https://gomami.io/store/hkg-pulse?aff=415)
