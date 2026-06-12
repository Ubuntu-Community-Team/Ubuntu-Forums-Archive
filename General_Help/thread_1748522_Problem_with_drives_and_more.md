---
title: "Problem with drives and more"
date: 2011-05-03
forum: General Help
---

### Post by Greezael on 2011-05-03
So I updated to Ubuntu 11.4 and everything went better than expected. As my computer is a pain to boot from usb, I did just an update and no fresh install. BUT

I discovered with horror that I couldn't see my other partitions, nor any connected pendrive. The Disk Utility didn't work, either. By using blkid (for a noob like me not easy to found xDD ) I saw that the drives were there and working, and I can even mount them manually. This is not the best option, as I use usb drives everytime. The drives don't even appear on Nautilus, I needed some time for realizing they were still there :(


Now, the weird thing. I finally decide to attempt a fresh install for getting rid of the problems. I found a reference to the Unetbooting trick for booting from an iso and ran the last iso I found (from today). In the live mode, the problem PERSISTS. Even when trying to install to hard disk, the installer cannot see any partition on my hard drive.

The setup is just a 200Gb SATA disk with a partition of 98Gb for linux (Ubuntu), a 2Gb for the Swap, and 2 50Gb partitions for Windows XP (wich recognize the pendrives, but has never managed to see the other partitions due the format) and another system (in this moment without anything). Till now I have used Ubuntu 10.4 and 10.10, without any kind of problems.

Any idea? Thanks in regard.

(And sorry for my english, native spanish ^^ Hope it is at least understandable)

---

### Post by Greezael on 2011-05-03
Bumping the thread and also adding: There is a strange floppy0 icon, referring to dev/fd0, but which cannot be mounted. I have a floppy disk unit, but never used it (only for booting, I mean that I have not installed any kind of strange drivers).

That's all, please HELP. This is really strange.

---

### Post by rwsmith61 on 2011-05-03
> **Greezael said:**
> . By using blkid (for a noob like me not easy to found xDD ) I saw that the drives were there and working, and I can even mount them manually. This is not the best option, as I use usb drives everytime. 

It sounds like you still have 11.04 installed. Try the following:

1) Use fdisk -l from the command line, for example:

> sudo fdisk -l /dev/sda

2) Install gparted (a graphical partition editor) 

Both of these will show you the partitions on the whole disk. To see which disks your system sees do:


> ls /dev/sd*

3) To see if your USB subsystem sees your pendrive do the following:

> lsusb

Look through the output to see if you can see the pendrive. lsusb without options will give you a summary of all your usb devices and hosts. lsusb -v will give alot of detail on each attached device.

4) Ubuntu will not automatically mount your XP (NTFS or FAT) partitions. Check your /etc/fstab for the partitions that Ubuntu will automatically mount at boot. Manually add your XP partitions on your SATA drive if you want them mounted automatically.

if you need more assistance please provide some more details of your system/hardware and the output of the above commands.

--bs

---

### Post by Greezael on 2011-05-04
First of all thanks for the answer. This are the dumps:

```
fdisk -l /dev/sda
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed939

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10942    87889920   83  Linux
/dev/sda2           10943       24316   107420673    5  Extended
/dev/sda3   *       12158       18237    48827392    b  W95 FAT32
/dev/sda5           10943       12158     9764864   82  Linux swap / Solaris
/dev/sda6           18237       24316    48827392   83  Linux

``````

ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdd  /dev/sdf  /dev/sdg1
/dev/sda1  /dev/sda3  /dev/sda6  /dev/sdc  /dev/sde  /dev/sdg

``````
lsusb
Bus 004 Device 002: ID 050d:705e Belkin Components F5D7050 Wireless G Adapter v5000 [Realtek RTL8187B]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:c002 Hewlett-Packard PhotoSmart 7800 series
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 002: ID 062a:6723 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 116f:c109 Silicon 10 Technology Corp. Flash Card Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```So, as you can see, it detects my drives correctly. The problem is: ¿Why it doesn't automount pendrives and similar? ¿Why my other partitions won't show up in Nautilus (so I can mount them easily)?

I can do the fstab thing, but before the update I didn't never have the need. And I'm worried about all this.

Thanks.

---

