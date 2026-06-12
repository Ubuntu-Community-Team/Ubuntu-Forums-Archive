---
title: "Ubuntu won't boot after trying installing a debian &quot;live usb&quot; on /dev/sda8"
date: 2011-10-09
forum: General Help
---

### Post by blackbird34 on 2011-10-09
Hi 
First time with Unetbootin and Debian, i downloaded the netinstall image and told it to put itself in /dev/sda8 instead of the recommended /dev/sdb_ (my external hard drive...)
Now when i start it goes past the first screen where you can access bios, but doesn't get to grub and just says something like "no system available. Please insert usb drive and press any key"

how can i get Grub and access to my system back? I have already REMOVED the /dev/sda8 partition and it still does the same thing...

---

### Post by blackbird34 on 2011-10-09
or, how could i remove unetbootin from my install from a live cd environment?

---

### Post by QLee on 2011-10-09
> **blackbird34 said:**
> or, how could i remove unetbootin from my install from a live cd environment?
I would guess that when you did what you did you allowed the MBR of your hard disk to be overwritten. You should read the instructions more carefully, that program is designed to make a bootable USB drive not to be written to a partition on a hard drive.

This thread about GRUB2  is what you need to restore your MBR on sda, but please read it carefully, there is more than just one thing discussed in the thread. 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-10-09
Do you still have your other partitions on the USSB drive? Most of the installers for liveCD assume small flash drives and the first thing they say is the entire drive will be erased.

Post this 

```
sudo fdisk -lu
```

If  install is ok you might not have to do the full chroot uninstall and reinstall. Thery or four similar ways:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot with screen shots

---

### Post by bob53124 on 2011-10-09
if you can't boot at all try reinstalling it with a cd i cant think of anything else u could do or you could try to boot up a live cd and when it comes up with the two little buttons at the bottom press the space button and then rescue a broken system

---

### Post by blackbird34 on 2011-10-09
I reinstalled before i could come back to the forum and see your answers... As i also use this computer for college 
It hadn't wiped my partition table for /dev/sda (my main hard drive), so I just reinstalled one of my Natty Narwhals and updated it back to normal, as it has a separate /home.
At least I know how to use Unetbootin now :)
Thankyou.

---

