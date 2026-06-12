---
title: "What program to make disk image of a Microdrive"
date: 2010-03-31
forum: General Help
---

### Post by johnvan on 2010-03-31
I use Ubuntu 9.04.
  I received a microdrive with a customized version of XP that I would like to save for reinstillation back onto the microdrive at a later date if I ever have problems.
What program in Ubuntu can I use to make an image of this microdrive?

Thanks

---

### Post by Bungler on 2010-03-31
I think you can make disk images with brasero, Although I'm not sure whether it will be able to copy the boot sector. Else you can use something like 'ghost 4 linux'

---

### Post by Ghost|BTFH on 2010-03-31
If you're talking about a data drive and not a CD/DVD, you're best bet would be to use gparted to copy the partitions to another drive (if possible) as that would be the most accurate way and would allow you to save boot flags, etc.

Otherwise, I suppose you could theoretically back it up as a DVD iso, however, restoring it would be another issue entirely.

Hope that helps.

Cheers,
Ghost|BTFH

---

### Post by ddarsow on 2010-03-31
use gparted. NOT Brasero.

---

