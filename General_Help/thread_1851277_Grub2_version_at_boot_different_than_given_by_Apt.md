---
title: "Grub2 version at boot different than given by Apt"
date: 2011-09-28
forum: General Help
---

### Post by jaredscribe on 2011-09-28
At Boot, The version of Grub displayed on the splash page is 1.97.
However, in synaptic or aptitude, the grub-pc and grub-common packages are given as 1.99rc1...

Does this mean the newer version is installed but not activated, or saved in the MBR?

11.04 Natty
Unity 2D
I have 10.04 installed on another partition.

---

### Post by jaredscribe on 2011-09-28
Ok, Figured out the problem.  I've been using the Grub2 bootloader in /dev/sda3 - Ubuntu 10.04, to boot into /dev/sda1 - Ubuntu 11.04.  Didn't realize I was doing this.  I also have Grub2 installed on /dev/sda1, where 11.04 is installed and those are the newer packages I was expecting to see in the boot menu.

Now I have a different task - to edit the MBR to point to the bootloader on /dev/sda1.  I'm going to spend some time getting to know the gnu grub manual and carry on this conversation in a different thread.

---

### Post by jaredscribe on 2011-09-28
[http://ubuntuforums.org/showthread.php?t=1851285]("http://ubuntuforums.org/showthread.php?t=1851285")
For anyone interested.

---

### Post by Quackers on 2011-09-28
Just boot into the operating system that you want to control grub and run ```
sudo grub-install /dev/sdX
``` where /dev/sdX is your boot drive.

---

### Post by hal8000 on 2011-09-28
> **jaredscribe said:**
> Ok, Figured out the problem.  I've been using the Grub2 bootloader in /dev/sda3 - Ubuntu 10.04, to boot into /dev/sda1 - Ubuntu 11.04.  Didn't realize I was doing this.  I also have Grub2 installed on /dev/sda1, where 11.04 is installed and those are the newer packages I was expecting to see in the boot menu.

Now I have a different task - to edit the MBR to point to the bootloader on /dev/sda1.  I'm going to spend some time getting to know the gnu grub manual and carry on this conversation in a different thread.

If you are trying to chainload from grub2 to grub1 (grub legacy) then they dont play well together.
Chainloading from grub legacy is easy and just a matter of editing /boot/grub/menu.lst:
Examples:
--snip--
title Windows Bootloader
root (hd0,1)
makeactive
chainloader +1

title FreeBSD
root (hd0,2)
makeactive
chainloader +1

Another thing I've found is that grub2 never picks up my FreeBSD and adds
it to grub2 menu. Hope that helps.

---

