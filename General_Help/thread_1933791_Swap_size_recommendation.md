---
title: "Swap size recommendation?"
date: 2012-03-01
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-03-01
I have 3 GB of RAM. What would be a good recommendation for swap size?

---

### Post by Tiganjero on 2012-03-01
The swap partition is used when you run out of physical memory. Which, in your case, if you have quality RAM, wouldn't happen that often, or at all. But since you're keen on adding it, I'd recommend using the same amount as the amount of RAM that you have, if you have that much space to spare that is, which is the case with most computers now-days.

Cheers,
George

---

### Post by MadsRC on 2012-03-01
I had people recommend me 1Gb of SWAP, but I always have the same amount of SWAP as RAM. So that'd be 4Gig in my current workmachine.

---

### Post by ryanmichaelmcclure on 2012-03-01
I'll go ahead and do 3...just in case. :) Thanks all.

---

### Post by HeroOfCanton on 2012-03-01
Minimum of 3GB with a "standard" being double your RAM, or 6GB, assuming you're not crunched for HDD space.

---

### Post by jerome1232 on 2012-03-01
> **Tiganjero said:**
> The swap partition is used when you run out of physical memory. Which, in your case, if you have quality RAM, wouldn't happen that often, or at all. But since you're keen on adding it, I'd recommend using the same amount as the amount of RAM that you have, if you have that much space to spare that is, which is the case with most computers now-days.

Cheers,
George

Not entirely true, ram not used by applications will be used as a file cache to speed up disk read/write operations, if your doing a lot of reading or writing from/to disk, unused application data in memory may be swapped in favor of more file cache. If your doing some heavy file operations, you will fill your ram with file cache very quickly.

That being said, only a small amount of swap space is needed to allow this to happen. I use 1/4 of my ram as swap right now.

---

