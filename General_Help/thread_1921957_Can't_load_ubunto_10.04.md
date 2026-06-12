---
title: "Can't load ubunto 10.04"
date: 2012-02-07
forum: General Help
---

### Post by graympa on 2012-02-07
I can boot from live CD, but can't install. Thought problem was my ATI Radeon HD 5450 graphics card, so after trying everything I could find on the forums I removed it. All I get is grub: . Don't know anything about grub.  The only linux distro I could get to load was Centos 5.7 (but would prefer Ubuntu). My questions are:
1. I had a bad virus that killed my Windows on another drive. Is the install reading the fact that I have NTFS file system on another drive and thinks I have Windows, and that is why grub hangs? What can I do about it.
2. Can anyone point me to a thread where I can fix my ATI graphics problem?
3. If not, what would be a good cheap choice to replace my graphic card (need 3D for some AutoCAD stuff I'm working on).

Thanks,

graympa

---

### Post by wildmanne39 on 2012-02-07
Hi, > Is the install reading the fact that I have NTFS file system on another drive and thinks I have Windows, and that is why grub hangs?No I doubt it.

Also you might have four primary partitions already if so you will need to delete one. Please post the output of:
```
sudo parted -l
```
and we can see if it is because of four primary partitions.

> 2. Can anyone point me to a thread where I can fix my ATI graphics problem?Try this to get ubuntu to install.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
> 3. If not, what would be a good cheap choice to replace my graphic card (need 3D for some AutoCAD stuff I'm working on).Nvidia cards are also a good choice just do not get an optimus card.

If none of these work please post the exact reason you can not install, what error messages you are getting.
Thanks

---

### Post by graympa on 2012-02-09
Thanks Wildmanne.  I had too many partitions, so I moved stuff around and deleted everything else, so I had 3 partitions. Still couldn't load, so I disconnected 2 of my hard drives, and then I was able to load. Will see what happens when I connect them back.

Thanks for the pointers!

---

### Post by wildmanne39 on 2012-02-09
Hi, your welcome!

---

