---
title: "partition for making dual boot"
date: 2010-06-16
forum: General Help
---

### Post by ukmad on 2010-06-16
I am already using ubuntu 9.10 for over six months but now i want make my system dual boot with windows as well.
How do i do it.
there are no partitions on my HDD all current space is dedicated to ubuntu only. 
Kindly help me on this

---

### Post by Jake007g on 2010-06-16
I'm not 100% sure, so don't guy purely by my word, but I'm pretty sure you'd go about it by just installing Windows (with advanced install options, to install it on a new partition), and then booting back into Ubuntu via a Live-CD and then reinstall grub as the bootloader so you can choose between Linux/Windows. 

Windows boot manager might even be able to let you choose between Linux/Windows, not too sure.

---

### Post by oldfred on 2010-06-16
Windows will only install to a primary partition. Have you used all the primary partitions?

I prefer grub to adding even another third party boot loader to make things more complex.

To see current partitions:
```
sudo fdisk -l
```

---

### Post by K.J. on 2010-06-16
If you boot from an Ubuntu Live CD or GPareted (which is a much smaller download), you can use gparted to resize and move your partitions to make room for Windows. However, you will have to reinstall grub after AND add a Windows entry.

The much easier route is to start from scratch. Backup your data and start by installing Windows.  Leave room on the drive for Ubuntu to install to.  Next, install ubuntu to that free space and Windows will automagically be added to the boot menu.

---

### Post by ukmad on 2010-06-17
> **oldfred said:**
> Windows will only install to a primary partition. Have you used all the primary partitions?

I prefer grub to adding even another third party boot loader to make things more complex.

To see current partitions:
```
sudo fdisk -l
```

this is what i get after fdisk
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095c79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60241   483885801   83  Linux
/dev/sda2           60242       60801     4498200    5  Extended
/dev/sda5           60242       60801     4498168+  82  Linux swap / Solaris

---

### Post by jesseafrantz on 2010-06-17
Well if you want to make another partition what I personally would do is use a program called "G-Parted". While in the program at the top right corner select your main HDD, you will see your partition, select it and select "Edit/Resize" and shrink it to have some space for windows, press apply, you will see it will say "Unallocated space" exit boot up in windows installation and select the unallocated space to install it in.

---

