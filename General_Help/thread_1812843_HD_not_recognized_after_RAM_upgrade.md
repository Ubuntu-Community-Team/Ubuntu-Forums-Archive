---
title: "HD not recognized after RAM upgrade"
date: 2011-07-26
forum: General Help
---

### Post by belfasttim on 2011-07-26
Hi-- I was trying to help my dad upgrade the RAM in his Toshiba laptop running Ubuntu 10.10. I checked on several websites to verify that I had got the proper RAM to upgrade from his 2x512MB to 2x1GB (his machine is old, max RAM is 2GB).

I swapped the RAM out and rebooted, as I've done many times on other machines, and nothing happened-- the HD light was lit, but nothing else, no bios messages, nothing, just a black screen.

I thought maybe I had bad RAM so I swapped in another set that I had, and this time it tried to boot, but when Ubuntu loaded it died with messages saying that it could not find/mount the hard drive.

I was able to put the original RAM back in and it worked fine. I'm pretty puzzled by this-- how could the RAM affect the HD? Is this a sign of needing to upgrade the BIOS or something?

Thanks for ideas.

---

### Post by |{urse on 2011-07-26
disregard this due to *forum blindness* :)

---

### Post by 2F4U on 2011-07-27
Maybe the second set of RAM is faulty? I/O addresses are mapped into an area of physical address space. So, if the RAM is faulty, every strange thing you could imagine can happen. If possible, run memtest on the second pair to see if it reports any problem. Run all the tests, even it takes a long time to complete.

---

### Post by dim_hyder on 2011-07-27
Hi,

If the original RAM is still available, can it be reinstalled? 

Does the laptop then work?

If not then it might be a case of opening up the laptop to check all cabling connections especially if the HDD is seated correctly.

Cheers,

Pete

---

