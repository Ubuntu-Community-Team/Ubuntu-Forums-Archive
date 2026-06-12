---
title: "Ubuntu not showing up for boot on dual boot system with XP pro"
date: 2010-09-13
forum: General Help
---

### Post by kitcarson61 on 2010-09-13
Please don't ask why as it was on instructions from "She-who-must-be-obeyed"'s orders.
I had to install XP Pro onto an unused partition of my hd to dual boot with Ubuntu 9.10.  It was an uneventful installation as those things go when dealing with a microshaft product, but after massaging out the bugs with XP, there was no option upon restart to boot to anything but XP.  The machine just automatically booted to XP.  
Now, here's where I feel even more the fool: during the XP install, a screen passed by saying something about changing the accessibility to the Ubuntu partitions, but that it could "easily" be changed somehow once XP was fully installed...I didn't write it down. I know, I know...  I'm not worthy of it, but, please, if there's someone out there who knows what's going on with this, please pity this old fool and offer up any advice you may have.  Thanks.

---

### Post by huzefa_from_kuwait on 2010-09-13
It has happened with me before, Mine was the case of Ubuntu 7.04 yours is XP, that is the only difference. You can follow the steps here.

[http://ubuntuforums.org/showthread.php?t=1174072](http://ubuntuforums.org/showthread.php?t=1174072)

---

### Post by oldfred on 2010-09-13
huzefa_from_kuwait is for grub legacy. 

If you have a newer install 9.10 or greater that was installed not upgraded you probably have grub2. The instructions to install grub back to the MBR are different for the different versions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by kitcarson61 on 2010-10-02
Actually guys, I ended up going back, wiping everything out, installing Microshaft first and followed with the 9.10 install to it's own partitions.  For some reason, that worked just fine.  I just figured I'd try that while waiting for a response and you guys were too fast with your responses, it there's such a thing as too fast.  Thanks for the help.

---

