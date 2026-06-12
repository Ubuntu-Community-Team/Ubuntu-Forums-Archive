---
title: "Unable to boot to Ubuntu after installing Win Xp"
date: 2010-10-07
forum: General Help
---

### Post by WannabeHammett on 2010-10-07
Hi,

I initially had Win XP Service pack 2 installed on my system. Then i installed the desktop version of Ubuntu 10.04 (dual boot). All was fine until then. I could access both.

Later on, i re-installed Win XP (excessive errors). After this I'm unable to boot into Ubuntu. The option that comes at the start 'Win Xp or Ubuntu' doesn't appear at all. System boots directly into XP.

But in the Administrative Tools > Disk Management option  under Win XP, there is an unknown partition of 15.3 GB. So i'm guessing Ubuntu still exists on my hard drive.  

Any way to bring Ubuntu back from the dead other than a re-install?

Thanks in advance :)

---

### Post by sikander3786 on 2010-10-07
You need to re-install the Ubuntu Bootloader i.e, Grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EasyBCD is another choice, but I'll prefer Grub.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Elfy on 2010-10-07
You need to reinstall grub - [How to restore the Ubuntu grub bootloader (9.10 and beyond)]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1")

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by soldier1st on 2010-10-07
you need to fix grub which you can do here [http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/](http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/)

---

