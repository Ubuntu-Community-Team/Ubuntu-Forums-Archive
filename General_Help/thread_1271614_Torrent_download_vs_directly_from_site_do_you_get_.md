---
title: "Torrent download vs directly from site? do you get the exact same file?"
date: 2009-09-21
forum: General Help
---

### Post by boyofford on 2009-09-21
Hi all, 

Just about to install ubuntu on new computer i'm getting today and i can't find my juanty 9.04 ubuntu disk so downloading again.

My question is do the direct download from ubuntu site and downloading as torrent result in the same iso?

i.e. are they both as up to date as each other?
Guessing they probably are as same checksum used, but thought i'd ask.

cheers
rich

---

### Post by nikhilk on 2009-09-21
> **boyofford said:**
> My question is do the direct download from ubuntu site and downloading as torrent result in the same iso?

i.e. are they both as up to date as each other?
Guessing they probably are as same checksum used, but thought i'd ask.

Yes, they should be the same and as you said, using checksum is the only sure way to confirm that.

---

### Post by boyofford on 2009-09-21
> **nikhilk said:**
> Yes, they should be the same and as you said, using checksum is the only sure way to confirm that.

Thanks for speedy reply!
Looks like theres no way to get around the fact that i'll need 5 months of updates lol!

---

### Post by BUSHYBOB on 2009-09-21
> **boyofford said:**
> 
Looks like theres no way to get around the fact that i'll need 5 months of updates lol!

You could wait 'til next month and get Karmic Koala when it comes out.

---

### Post by egalvan on 2009-09-21
> **boyofford said:**
> 
My question is do the direct download from ubuntu site and downloading as torrent result in the same iso?


They are the same file, only the download mechanism is different.

One major advantage to torrent is that the load is taken off the down-load servers and spread over a much larger pool of 'servers'.

Another major advantage to using torrent is the automatic checking built into the torrent mechanism.
Files are broken into 'pieces' or 'chunks' of 256K bytes.
It check-sums each "chunk" of the file as it is received.
If the check-sum fails, it is re-sent.
One bad byte only results in that particular pieced being re-sent.
This means that the complete file has an extremely high probability of being error-free.

On a direct download, the entire file must be received before it can be checked for integrity 9usually using md5 or sha).
One bad byte will result in a bad download, and the entire file will need to be downloaded again.

---

### Post by 3rdalbum on 2009-09-21
They are definitely the same. I downloaded the ISO from my ISP's free Ubuntu mirror, and started seeding it on the torrent.

---

