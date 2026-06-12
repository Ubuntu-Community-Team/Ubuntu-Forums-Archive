---
title: "HDD booting"
date: 2010-01-08
forum: General Help
---

### Post by nemiux on 2010-01-08
Hey everyone, I'm getting a new HDD today.
I have SATA 500GB, and I'm getting SATA II 500gb.
This is what I wanted to ask.
On my first HDD, I have Windows XP and ubuntu,  and on the new HDD, I will install Windows 7. What I wanted to ask, are such things like jumpers on my HDD (master/slave etc.) used to select boot order? Or will I have to go into BOOT settings, and choose Win7 Hdd first in the boot order etc.?
Thank you.

---

### Post by nemiux on 2010-01-08
I also wanted to ask. In my chipset scheme, I have Sata 2, 3, 4, 5. and eSata. Will I be able to use Sata II?

---

### Post by falconindy on 2010-01-08
The jumpers used on IDE drives aren't used on SATA drives. The BIOS controls the boot order.

> In my chipset scheme, I have Sata 2, 3, 4, 5. and eSata.
You likely have SATA **ports** labelled 2, 3, 4, 5 and eSata. The latest standard of SATA is at the 3rd revision (might also see it as SATA 6.0gb/s). However, SATA II and III drives are fully backwards compatible and will run as fast as the interface provided. In other words, a SATA II disk can and will run on a SATA I bus, but just not as quickly.

---

