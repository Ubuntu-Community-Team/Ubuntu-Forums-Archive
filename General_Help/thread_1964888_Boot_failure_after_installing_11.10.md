---
title: "Boot failure after installing 11.10"
date: 2012-04-24
forum: General Help
---

### Post by narsil4 on 2012-04-24
bootinfoscript output: [http://paste.ubuntu.com/944720/](http://paste.ubuntu.com/944720/) 

Downloaded ubuntu-11.10-desktop-i386.iso via torrent and burned to DVD.

Booted disc, created partitions, began installing, then realized I hadn't
created enough swap space.

Powered off, began install again, this time selecting the "whole drive" option
without manual partitioning. The installer reported success. The hard drive 
was thereafter unbootable, with message: 

"Reboot and Select proper Boot device or Insert Boot Media..."

Ran the installer again, partitioned manually (just for something different). The
installer completed again. The result was the same: an unbootable hard drive
with message "Reboot and Select proper...".

Brand new Gateway FX6860-UR20P

Processor & Chipset  
Number of Processors Installed    1
Processor Manufacturer    Intel
Processor Type    Core i7
Processor Model    i7-2600
Processor Core    Quad-core (4 Core)
Processor Speed    3.40 GHz
Cache    8 MB
64-bit Processing    Yes
Hyper-Threading    Yes
Chipset Manufacturer    Intel
Chipset Model    H67 Express

Memory  
Standard Memory    8 GB
Maximum Memory    8 GB
Memory Technology    DDR3 SDRAM
Memory Standard    DDR3-1333/PC3-10600
Number of Total Memory Slots    4
Memory Card Reader    Yes

Storage  
Number of Hard Drives    1
Total Hard Drive Capacity    1.50 TB
Hard Drive Interface    Serial ATA
Hard Drive RPM    7200
Optical Drive Type    DVD-Writer
Optical Media Supported    DVD-RAM/±R/±RW
Controllers  
Controller Type    Serial ATA

Display & Graphics  
Graphics Controller Manufacturer    ATi
Graphics Controller Model    Radeon HD 6750
Graphics Memory Capacity    1 GB
Network & Communication  
Ethernet Technology    Gigabit Ethernet
Wi-Fi    Yes
Wi-Fi Standard    IEEE 802.11b/g/n

Interfaces/Ports  
HDMI    Yes
DVI    Yes
Total Number of USB Ports    10
Number of USB 2.0 Ports    10
Network (RJ-45)    Yes
Audio Line In    Yes
Audio Line Out    Yes
VGA    Yes

---

### Post by strask on 2012-04-24
Is it possible your computer is trying to boot off a USB device? Make sure you unplug any USB devices then try rebooting again.

---

### Post by oldfred on 2012-04-24
Two things. There was (is) a bug in grub that with very large / (root) partitions it just gets lost. I have suggested as a test just shrinking root to a much smaller size and most can boot. My normal suggestion for / is 25GB with the rest as /home, but with a drive as large as yours you may want additional partitions.

Second with gpt partitions your need another small 1MB bios_grub partition. It can be anywhere on drive, so just add it. If system UEFI capable? If you you should add a efi partition but that does have to be first.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02. Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.


In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by narsil4 on 2012-04-24
oldfred, thank very much you for the detailed response.

Is the GUI partition creator in the 11.10 install CD useless to me, then? Or will it work if I create a smaller root partition along with possibly other things you suggest?

My last encounter with this stuff was during the time of LILO. I think it will take a day or more of studying in order to understand exactly what to do with these newfangled contraptions.

Can you can suggest a path which is (as Yoda says) "quicker, easier, more seductive"? For example I don't care about using all the disk -- would using only the first, say, 700MB get around the problem?

---

### Post by narsil4 on 2012-04-24
> **strask said:**
> Is it possible your computer is trying to boot off a USB device? Make sure you unplug any USB devices then try rebooting again.
A good suggestion, but I'm certain no USB devices were attached, and the boot menu did not list any.

---

### Post by strask on 2012-04-24
> **narsil4 said:**
> A good suggestion, but I'm certain no USB devices were attached, and the boot menu did not list any.

I just thought that because your boot info script output listed a /dev/sdg that looked like a thumb drive; but maybe that wasn't plugged in when you got the boot failure. :)

---

### Post by oldfred on 2012-04-24
I always have created partitions in advance with gparted, but since using gpt(GUID) you have to change the default from MBR(msdos).

You should be able to just create smaller / partition as part of the install and a separate /home. I only use about 7GB in / with all my data in separate data partitions.

I might do this, if you think drive will be ever used in an UEFI system. If not leave off the first partition but it is small so hardly matters.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
   250 MB efi FAT32 Must be first partition with "boot flag"
     1 MB bios_grub  no format 
 25 GB Mountpoint / beginning ext4(or ext3)
all but 2 GB Mountpoint /home  beginning ext4(or ext3)
 2 GB Mountpoint swap 

Leave some space unallocated for now if not sure what you what to do. One advantage of gpt is all partitions are primary. With gpt you will not be able to install Windows unless UEFI booting. So if thinking of Windows ever, then use MBR not gpt.

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

In GPT fdisk (gdisk), ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by narsil4 on 2012-04-24
Before I saw oldfred's last response I attempted to install again, this time with 25GB root, 500GB home, and 24GB swap, all configured with the GUI partition program in the installer. Still the same boot failure. [http://paste.ubuntu.com/944957/](http://paste.ubuntu.com/944957/)

This is a new machine which came with Windows 7 installed. I burned the Ubuntu DVD using WIndows and elected to erase Windows during the first Ubuntu install. Since I have only one DVD drive, and since the live DVD renders the DVD drive inaccessible, I cannot burn PartedMagic as one link suggested. Also, I cannot burn to my USB stick ([http://ubuntuforums.org/showthread.php?t=1964914](http://ubuntuforums.org/showthread.php?t=1964914)).

I have gparted on the live CD, but it seems to be the wrong tool. I begin as oldfred suggested with a fat32 partition, but the right-click menu on that partition has the "Manage Flags" action grayed out. It's not clear how to get gpt,

```
ubuntu@ubuntu:~$ gpt
The program 'gpt' is currently not installed.  You can install it by typing:
sudo apt-get install gpt
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install gpt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gpt

```

The same for gdisk. Thus I seem to be stranded with a 11.10 install CD. I am a bit overwhelmed because I have no idea how I'm going to achieve what oldfred suggests -- do I use gpt, or gdisk, or both? Is installing Ubuntu -- or any Linux distribution -- even possible at this point using only what I have?

---

### Post by narsil4 on 2012-04-24
Alright, I was able to burn to my USB drive, so presumably I can use that to burn DVDs or vice versa.

However it's still not clear what I need to do. Do I start with PartedMagic? It seems the process should be straightforward, but I foresee many hours of learning before knowing what action to take.

---

### Post by oldfred on 2012-04-24
In gparted you click on Device, but then have to use advanced and choose gpt. A bios_grub partition has no format so it will show a warning/error in most tools -ef02 in gdisk. You select a boot flag for an efi partition (But it is not a boot flag in gpt is ef00 in gdisk).

I have not used gdisk, it is a command tool like fdisk. 

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

From gdisk the same as the attached gparted SSD drive formated with gpt partitions.
fred@fred-Precise:~$ gdisk -l /dev/sde
GPT fdisk (gdisk) version 0.8.1

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sde
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  10
```

---

### Post by narsil4 on 2012-04-25
I was about to dive into following oldfred's suggestions when I decided to try a 12.04 daily build from [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current) and ... it worked! I am typing from the new install, my first successful boot from the hard drive.

Thanks to all who responded.

---

### Post by strask on 2012-04-25
Congratulations!

---

