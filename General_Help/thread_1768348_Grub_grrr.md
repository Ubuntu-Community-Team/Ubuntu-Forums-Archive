---
title: "Grub grrr"
date: 2011-05-26
forum: General Help
---

### Post by Zerocool Djx on 2011-05-26
What is the proper way to install ubuntu on secondary HD with grub loader installed choosing between that and win 7 on primary hd?

---

### Post by noah++ on 2011-05-26
Ubuntu will set it up properly during install?

---

### Post by oldfred on 2011-05-26
You have to partition in advance and/or partition as part of the manual install (Something Else in Natty). Then you get the choice on where to install grub2's boot loader and you want to install it to the same drive as your Ubuntu install. Then set that drive to boot in BIOS.

While screens shown are Maverick the changes to the process are minor.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Zerocool Djx on 2011-05-26
> **noah++ said:**
> Ubuntu will set it up properly during install?

No, if you use the secondary drive it won't install grub

---

### Post by oldfred on 2011-05-26
I install to sdc partition and it defaults to sda which I let it as I boot either sdb or sdc in BIOS. That is even with manual install unless you change to to the same drive you install Ubuntu to using the combo box on manual install partition screen.

---

