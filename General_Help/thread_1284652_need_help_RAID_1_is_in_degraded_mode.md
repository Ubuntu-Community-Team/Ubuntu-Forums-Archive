---
title: "need help RAID 1 is in degraded mode"
date: 2009-10-06
forum: General Help
---

### Post by catman711 on 2009-10-06
I just did a new install of Jaunty using "alt. x64 desktop" disk as RAID 1. All went fine and works great, except it boots in degraded mode. I used this [https://help.ubuntu.com/9.04/serverg...tallation.html]("https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html") and followed to the letter.

I am a noob to Linux, but not computers. I did the normal diagnostics. I checked drives and cables. I can boot to desktop with ether drive connected to any port on MB. If both drives are connected it boots fine, but still shows degraded. 

If I run "sudo mdadm -D /dev/md1" with single drive (ether one) this is what get
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130777&thumb=1&d=1254695296[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=130777&d=1254695296")

If I run "sudo mdadm -D /dev/md1" with both drives this is what I get
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130778&thumb=1&d=1254695637[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=130778&d=1254695637")

If I run "cat /proc/mdstat" with both drives this is what I get
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130780&thumb=1&d=1254695906[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=130780&d=1254695906")

I don't know how to find out which drive it is not recognizing or why.

Any help would be great

I looked ad mdadm wiki and it tells how to replace a failed drive, but I don,t know how to tell which drive is failed.

Please, if you give me code to run, give me a disc. of what it dose. I would like to LEARN what I am doing, not just "do this" That way I will know to do next time, or be able to help someone else.

AMD Athlon x2 500+
Gigiabyte GA-MA69VM-S2 AMD 690V/SB600
4GB ram

Thanks, Mike

---

### Post by dcstar on 2009-10-06
> **catman711 said:**
> I just did a new install of Jaunty using "alt. x64 desktop" disk as RAID 1. All went fine and works great, except it boots in degraded mode. I used this [https://help.ubuntu.com/9.04/serverg...tallation.html]("https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html") and followed to the letter.

I am a noob to Linux, but not computers. I did the normal diagnostics. I checked drives and cables. I can boot to desktop with ether drive connected to any port on MB. If both drives are connected it boots fine, but still shows degraded. 
........

As the instructions says:

*Sometimes a disk can change to a faulty state even though there is nothing physically wrong with the drive. It is usually worthwhile to remove the drive from the array then re-add it. This will cause the drive to re-sync with the array. If the drive will not sync with the array, it is a good indication of hardware failure.*

---

### Post by catman711 on 2009-10-07
David,
Thanks for the quick response.
I did read that, but how do I remove and re-add it? 
I think it would be /dev/sda1. If I have 1 drive connected (ether one) it shows up as /dev/sda2.

I did search in forum,Google,ect... but most results had nothing to do with my problem, or assumed I knew more than I do.

Thanks
Mike

---

