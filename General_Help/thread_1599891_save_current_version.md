---
title: "save current version?"
date: 2010-10-18
forum: General Help
---

### Post by soarescv on 2010-10-18
The answer to this is probably somewhere around here, but I'm a n00b and really didn't know the correct keywords to find it, so maybe you guys can lead me in the right direction...

How do I save my current settings/configurations so that I have multiple stable versions on my bootloader?  

I want to have several iterative versions in case I royally screw one up, I'll have a stable one to go back to.  I ask because I already did the royal screw up once and had to reinstall completely. Btw, running Ubuntu 10.10, 64-bit.

Thanks,
yet another n00b

---

### Post by Rubi1200 on 2010-10-18
Hi and welcome to the forums :)

After each kernel update an entry is added to the GRUB bootloader along with the Recovery Mode option.

Practically speaking that means that if the latest kernel is, just an example, 2.6.32-25, and the previous kernel was 2.6.32-24, then you should see 4 entries in the GRUB menu (one for each kernel and one for each Recovery Mode). As more kernel updates become available, you will see the entries in the GRUB menu growing.

All your settings and configurations remain the same, only the kernel version changes.

Some people like to have a clean menu and clear out older kernel entries.

However, it is advisable to keep at least one previous version to boot into should, as you point out, something go wrong and you need to troubleshoot.

Hope this helps.

---

### Post by soarescv on 2010-10-19
It does, thanks for the response.

---

