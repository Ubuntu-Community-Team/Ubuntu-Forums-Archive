---
title: "Ubuntu boot freeze 9.04 on old HW"
date: 2009-11-28
forum: General Help
---

### Post by raczatt on 2009-11-28
Hi All,

I have and old desktop with Pentium III 667 MHz, 512 MB RAM and 20GB Quantum Fireball HDD.

Originally it had Ubuntu 8.10 for a year and some weeks ago completely reinstalled to 9.04. Everything was fine. 

1) Since 2 days when I try to boot both the normal and safe mode freezes _before_ getting to the login screen. In normal mode the Ubuntu screen w/ the progress-bar appears and immediately freezes. 

2) Memtest86 (v2.11) is over w/ "Pass complete, no errors"

3) After running Memtest86 for 1-2 hours tried booting in safe mode and fortunately it worked. Ran dpkg and fsck successfully.

So now my system is up but I don't have any know-how to investigate the logfiles etc...


Any idea is highly appreciated what can cause this boot hang, what to check / run.

Thanks,

---

### Post by spiderbatdad on 2009-11-28
dmesg (diagnostic message) can he very helpful. It is written by the kernel during boot and in run time, for example when a device encounters an error.
Run this in your terminal and  look through the file.```
dmesg > ~/Desktop.dmesg.txt
```

---

### Post by raczatt on 2009-11-29
I have checked dmesg but that showed the result of a successful boot
and not the couple of previous freezes.

Today it hung again. Ran Memtest86 for only 1 minute and after that it booted correctly. Really strange. It seems as if Memtest86 would do something that "enables" boot. Have no idea.

---

