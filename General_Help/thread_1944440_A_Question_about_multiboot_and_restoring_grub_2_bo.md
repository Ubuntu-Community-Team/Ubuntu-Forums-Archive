---
title: "A Question about multiboot and restoring grub 2 bootloader"
date: 2012-03-21
forum: General Help
---

### Post by neo1691 on 2012-03-21
Hey folks!! 

I have installed ubuntu 10.04 LTS alongside windows 7. The Grub 2 is the default bootloader. 

Here is a gparted screenshot of my system.

[CENTER][IMG]http://i.minus.com/i6F3wW2GKEz63.png[/IMG][/CENTER]

I plan to shrink one ntfs partition and install windows XP in that.
But i believe that it will completely wipe off the GRUP 2 bootloader.

So i would like to know that would i be able to get back the grup bootloader and will it be possible to add entries of both windows 7 and windows XP to it?? 

I have a bootable USB of ubuntu live!! 

PS: I am a n00b in terminal and very new to linux!! Thanks! :p

---

### Post by oldfred on 2012-03-21
Windows only boots from the active partition (boot flag). So it has to move the boot files from any additional installs to the first install and reconfigure to boot from the boot partition. 

Windows will only boot from one primary NTFS partition, so grub only finds the one with the boot flag and all the boot files. But there is a work around if you want two entries in grub (but then Windows will not boot both directly, you can manually move boot flag if you want).

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by neo1691 on 2012-03-21
> **oldfred said:**
> Windows only boots from the active partition (boot flag). So it has to move the boot files from any additional installs to the first install and reconfigure to boot from the boot partition. 

Windows will only boot from one primary NTFS partition, so grub only finds the one with the boot flag and all the boot files. But there is a work around if you want two entries in grub (but then Windows will not boot both directly, you can manually move boot flag if you want).

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)
Great!! Thanks!! I hope i can make it through!!


Can somebody clear this to me??


> **mahiyar said:**
> Ok. Success, without a hitch. Disconnected the original drive, connected the second smaller drive, installed windows 7 on it, reconnected the back the original drive (keeping the smaller one), made it bootable, booted to Ubuntu ran update-grub, win 7 discovered, that was all, now I have ubuntu 9.10, winxp and win7 from single menu. grub2 is really powerfull. Marking the thread as solved.


Came from one of those links!! I am unable to understand it!

---

