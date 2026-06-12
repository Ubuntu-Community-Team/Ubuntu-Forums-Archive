---
title: "How to get to Windows 7 Advanced Boot Options from GRUB"
date: 2011-02-06
forum: General Help
---

### Post by MrStill on 2011-02-06
I am looking at this computer, running Ubuntu 10.10 and Windows 7, Home Premium with GRUB 2 as the boot loader. I am looking to get to the Windows 7 advanced boot options screen; however I think it requires the windows boot loader to do so.

Any advice would be great...

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-02-06
as far as i know all grub can do to windows is point it at the windows partition and let it take over
when you select win 7 start slapping F8
you can always kill the power while windows is booting and it will bring up the options on next boot

---

### Post by MrStill on 2011-02-06
Thanks, we tried the F8 thing, and it seems to be a Windows boot loader control. As far as killing the power, the boot error screen doesn't give us the option for which we are searching.

---

### Post by Ghillie021 on 2011-12-20
Having had the same problem, I needed to load the Windows Advanced Boot Options too.

I managed to load it successfully through the Grub 2 Bootloader through tapping 'F8' immadiately after (even as) you select your Windows operating system to boot.

It seems as though the period you have to press it is very short which causes most people to miss it and presume that it is not possible.

Dealing with my own BSOD atm  :shock:

---

