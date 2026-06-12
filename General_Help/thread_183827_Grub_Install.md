---
title: "Grub Install"
date: 2006-05-28
forum: General Help
---

### Post by birdman on 2006-05-28
During Installation I am not given a choice of location for the boot loader.  I don't wan to install it to MBR.  How can I install it to the Ubunto Boot partition??
In other Distro's. Ive been given this option which works well for my Duel Boot using Acronis OS Selector.  Can you help me?

Thanks
Birdman

---

### Post by Sutekh on 2006-05-28
You can in the Ubuntu installation.  When it asks if you want to install GRUB to the MBR, say No and then provide the location of the Ubuntu installation and it will put GRUB there, ie /dev/hda1 for example.

The step looks like this, from the [best dual boot guide around](http://users.bigpond.net.au/hermanzone/)

[Install step - GRUB install]("http://users.bigpond.net.au/hermanzone/p3/34ntfs.gif")

---

### Post by birdman on 2006-05-28
Thanks for the info, its great but I have found that the problem is that Ubuntu is not seeing my Windows XP installation, thus I am not being asked if it is OK to install Grub.  It just does it.
Can anyone tell me why Ubuntu is not recognising my XP installation?
Fedora & SUSE have no problems.

---

### Post by Sutekh on 2006-05-28
[quote=birdman]Thanks for the info, its great but I have found that the problem is that Ubuntu is not seeing my Windows XP installation, thus I am not being asked if it is OK to install Grub.  It just does it.
Can anyone tell me why Ubuntu is not recognising my XP installation?
Fedora & SUSE have no problems.[/quote]
Unusual that GRUB should be unable to see WinXP.  Why do you not want GRUB on the MBR?


What you could do is let GRUB install on the MBR, then use a Windows recovery console to restore the Windows bootloader to the MBR (using **fixmbr**).  

Finally you can use an Ubuntu recovery console to reinstall GRUB, only this time to the place you want it.

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

Bit messy though.

---

### Post by birdman on 2006-05-29
Thankyou Sutekh, you have solved the problem.

Regards
Birdman

---

### Post by Sutekh on 2006-05-29
[quote=birdman]Thankyou Sutekh, you have solved the problem.

Regards
Birdman[/quote] Oh already?  Right on! 

Not a problem for my part, glad it worked out.

---

