---
title: "Live Ubuntu Patition?"
date: 2010-10-09
forum: General Help
---

### Post by SirRedTooth on 2010-10-09
I really cannot get hold of a large CD or USB.

How would I go about installing Ubuntu Live or GParted live on a partition.
Adding the new partition to grub1.98 booting off it and editing my windows + ubuntu partition?


This would also help very much because I wouldn't have to find and put in a live CD/USB everytime I want to change my ubuntu partition or restore any damaged OS installs as I would already have everything I need in a seperate partition which I can boot on Grub.

(Is this even possible?)

---

### Post by indytim on 2010-10-09
It's called installing Ubuntu to your hard drive!

At the LiveCD bootup, select the "Install" icon and proceed to install Ubuntu to your harddrive.

IndyTim

---

### Post by SirRedTooth on 2010-10-09
> **indytim said:**
> It's called installing Ubuntu to your hard drive!

At the LiveCD bootup, select the "Install" icon and proceed to install Ubuntu to your harddrive.

IndyTim
The problem is that I dont have a CD/USB to boot from.
So can I install Gparted or something similar to another partition (from my current ubuntu partition) then boot off it and use it to resize the very ubuntu partition I used to install it?

---

### Post by SirRedTooth on 2010-10-15
bump, still haven't found a solution

---

### Post by VMC on 2010-10-15
> **SirRedTooth said:**
> I really cannot get hold of a large CD or USB.

How would I go about installing Ubuntu Live or GParted live on a partition.
Adding the new partition to grub1.98 booting off it and editing my windows + ubuntu partition?


This would also help very much because I wouldn't have to find and put in a live CD/USB everytime I want to change my ubuntu partition or restore any damaged OS installs as I would already have everything I need in a seperate partition which I can boot on Grub.

(Is this even possible?)
How about booting it using the loop, as in this:

```
menuentry "Ubuntu Live" {
  loopback loop (hd1,8)/lucid-desktop-i386.iso
  linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso --
  initrd (loop)/casper/initrd.lz
}
```

You need to point the loop to the correct file and hard drive location

---

### Post by oldfred on 2010-10-15
If you can create a new small 1GB partition you may be able to use it like the USB install. 

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
Says you can install from same partition you boot from with workarounds.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

