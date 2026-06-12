---
title: "grub loading .. error 17 when comp boots"
date: 2009-12-29
forum: General Help
---

### Post by rycharlind on 2009-12-29
I was messing around with windows disk manager and deleted the partition that was holding my Ubuntu on it. Anyways, when I turn on my comptuer now the boot menu wont even show up. It just says
 
grub loading ...
error 17.
 
So now I cant even select to boot into Windows 7. Any suggestions other than booting from a usb or cd and doing a reinstall?

---

### Post by Leppie on 2009-12-29
boot using the ubuntu livecd, then go to System>Administration>Software Sources and activate the "universe" repository on the 2ubuntu software" tab and close.
open a terminal and issue these commands:
```
$sudo apt-get install ms-sys
$sudo ms-sys -m /dev/sda
```

---

