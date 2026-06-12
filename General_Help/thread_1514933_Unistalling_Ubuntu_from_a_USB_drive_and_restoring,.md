---
title: "Unistalling Ubuntu from a USB drive and restoring, Help!!!"
date: 2010-06-21
forum: General Help
---

### Post by mpparvez on 2010-06-21
Hi, I'm a new user of Ubuntu, so for testing it out, I installed Ubuntu on my USB drive (4 Gigs). I had Windows installed on my HDD. After using Ubuntu for afew days I found out that I am more dependent upon Windows (Mostly for games) and came to a conclusion that Ubuntu is not for me (till now). So I'd want to remove the GRUB boot loader and replace it with my normal Windows boot loader. HELP!!! 

Thanks...):P

---

### Post by C.S.Cameron on 2010-06-21
Do you mean you need your flash drive plugged in to boot Windows?
This would mean that you did a full install to your flash drive without using the advanced button?
If you have your Windows boot CD you should be able to run Emergency Console and type "fixmbr"

To fix it using the Ubuntu Live CD there is ms-sys

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

ms-sys may be hard to find but it has worked for me.

---

### Post by garvinrick4 on 2010-06-21
I got this off the Forums a few days ago for Ubuntu Live Cd to install Windows bootloader.


You first need to restore the windows boot loader. You can run fixMBR from a windows repair disk or from Ubuntu liveCD.

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR



[URL="http://ubuntuforums.org/showthread.php?t=1014708"]Here is also a site for using Windows disks to reinstall
[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=1014708"]
[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=1014708"]
[/URL]

---

