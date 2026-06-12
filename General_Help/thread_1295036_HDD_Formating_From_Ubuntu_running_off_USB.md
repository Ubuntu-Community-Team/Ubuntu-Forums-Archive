---
title: "HDD Formating From Ubuntu running off USB"
date: 2009-10-19
forum: General Help
---

### Post by vurwolf on 2009-10-19
Hey,

I have a 120 GB HDD That has Windows Vista on it. (Which totally sucks BTW) I want to format the whole HDD and install a fresh Ubuntu. How do I go about doing that? I tried going into gparted but it won't recognize the HDD.

Please help
Thanks

---

### Post by geirha on 2009-10-19
It doesn't show up at all? could you provide the output of the following two commands?
```
sudo fdisk -l
lspci
```

Also, which version of Ubuntu are we talking about?

---

### Post by vurwolf on 2009-10-19
> **geirha said:**
> It doesn't show up at all? could you provide the output of the following two commands?
```
sudo fdisk -l
lspci
```

Also, which version of Ubuntu are we talking about?

**This is the output for both of those Also I'm pretty sure it's Ubuntu 8.04**

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ lspc1
bash: lspc1: command not found
ubuntu@ubuntu:~$

---

### Post by lidex on 2009-10-19
Probably easier to download and burn a ubuntu live-cd and boot from it. The installer will allow you to partition your drive to your liking.

---

### Post by P4man on 2009-10-19
> **vurwolf said:**
> **This is the output for both of those Also I'm pretty sure it's Ubuntu 8.04**

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ lspc1
bash: lspc1: command not found
ubuntu@ubuntu:~$

youre mistyping. those commands have only letters, no numbers. So its FDiSK -L  in lowercase ans LSPCi in lowercase

---

### Post by mike555 on 2009-10-19
you might want a newer version of gparted , I suggest " Parted Magic" cd ....

---

### Post by vurwolf on 2009-10-19
> **P4man said:**
> youre mistyping. those commands have only letters, no numbers. So its FDiSK -L  in lowercase ans LSPCi in lowercase

ok I think I did it right this time. 
Below is what the output was


> 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6cd6a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS

Disk /dev/sdb: 8040 MB, 8040480256 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839698    b  W95 FAT32
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
ubuntu@ubuntu:~$ 


---

### Post by geirha on 2009-10-19
According to that output, there's a 120GiB harddrive (/dev/sda) with one NTFS partition, and an 8GiB drive (dev/sdb) with a FAT32 partition (your usb drive most likely).

That means it's not a driver issue (which is good). It's odd that gparted doesn't see it. Could you perhaps take a screenshot of gparted? Hitting Alt+PrtScr while the gparted window is the active window will take a screenshot of it. You can either add it as an attachement to a post, or upload it at [http://tinyurl.com/imagebin](http://tinyurl.com/imagebin) and provide the URL here.

Also, you don't need to partition it manually. The Ubuntu installer will give you the option to install Ubuntu on the whole drive (wiping whatever was there before).

---

### Post by vurwolf on 2009-10-19
> **geirha said:**
> According to that output, there's a 120GiB harddrive (/dev/sda) with one NTFS partition, and an 8GiB drive (dev/sdb) with a FAT32 partition (your usb drive most likely).

That means it's not a driver issue (which is good). It's odd that gparted doesn't see it. Could you perhaps take a screenshot of gparted? Hitting Alt+PrtScr while the gparted window is the active window will take a screenshot of it. You can either add it as an attachement to a post, or upload it at [http://tinyurl.com/imagebin](http://tinyurl.com/imagebin) and provide the URL here.

Also, you don't need to partition it manually. The Ubuntu installer will give you the option to install Ubuntu on the whole drive (wiping whatever was there before).


I've had gparted running for like 30 min now and it was still scanning all devices.

Also when I go to install Ubuntu I get to the 3rd step where i pick my keyboard settings and than it will not go any further than that, it just stops.

Here is the picture
[IMG]http://imagebin.org/index.php?mode=image&id=68410[/IMG]

---

### Post by P4man on 2009-10-19
gparted isnt starting for some reason. probably choking trying to read a cdrom or something?

Try this in a terminal:
```

gksudo gparted /dev/sda
```

or to perhaps catch the problem

```
gksudo gparted 
```

The last command wont work any better than what youre trying now, but the output might reveal the cause of the problem

---

### Post by vurwolf on 2009-10-19
> **P4man said:**
> gparted isnt starting for some reason. probably choking trying to read a cdrom or something?

Try this in a terminal:
```

gksudo gparted /dev/sda
```

or to perhaps catch the problem

```
gksudo gparted 
```

The last command wont work any better than what youre trying now, but the output might reveal the cause of the problem


Both out puts are the same 

> ubuntu@ubuntu:~$ gksudo gparted /dev/sda
======================
libparted : 1.7.1
======================
  


> ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 1.7.1
======================
  


---

### Post by P4man on 2009-10-19
Is that from a livecd? Which version?

I found this bug that sound a lot like it, but its from very early Karmic:

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/374579](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/374579)

---

### Post by vurwolf on 2009-10-19
I'm Running Ubuntu off my USB Drive I wrote the ISO to it so it is bootable. The ISO I wrote to it is ubuntu-8.04.1-desktop-i386.iso

---

### Post by P4man on 2009-10-19
Can you try a newer version of ubuntu?
If not, you could try opening synaptic and updating just those packages listed in that bug report. Those updates wont be persistent though.

---

### Post by vurwolf on 2009-10-19
I just updated all those and so far I see no difference in anything. Gparted is still Scanning all devices....

I think I might have stumped everyone with this one.

---

### Post by P4man on 2009-10-19
actually.. since you just want to nuke the partition, you could try this:

```
sudo parted /dev/sda mkfs 1 Ext3

```

hoping that wont stall and that the commands I gave are correct. for obvious reasons im not going to test it here :)  After that perhaps gparted will also work,

**WARNING** that will format your sda drive, all data on it will be wiped!

---

