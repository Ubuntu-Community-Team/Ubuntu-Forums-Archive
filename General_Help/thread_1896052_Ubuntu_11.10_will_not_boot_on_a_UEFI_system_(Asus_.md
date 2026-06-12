---
title: "Ubuntu 11.10 will not boot on a UEFI system (Asus P8H61-I)"
date: 2011-12-16
forum: General Help
---

### Post by Ubutuxer on 2011-12-16
This problem is driving me crazy. I have tried everything. Searching online for a solution for weeks and trying to boot the internal SSD disk with a USB stick.


**To the problem**
Ubuntu 11.10 boots and installs without any errors from the original ISO image extracted on a USB stick (using Ubuntu's own "Create bootable stick" program).

When I reboot the PC after installation, I get only a black screen after the Asus logos with a blinking cursor. No errors from the EFI/BIOS, nothing to indicate me in any direction.

I also tried some of the daily builds of 12.04 with the same results. But booting from USB does work without any issues, as long as you select the UEFI version of the stick showing up in the Asus EZ settings.


[B]Question 1
[/B]Is it possible to get Ubuntu 11.10 or 12.04 to boot from the SSD disk on Asus P8H61-I motherboard? How?

I've already tested the SATA settings, IDE, Compatible and AHCI. Nothing helps. I re-installed Ubuntu between every change.


[B]Question 2
[/B]I'd be perfectly happy to use a USB stick as a loader for the actual OS residing on the SSD as long as it just boots. I could then wait for a next Ubuntu release which should (at some point) add a proper UEFI support.

But I've been unable to load the OS from the internal drive with a stick because GRUB or the Linux kernel claims that it is unable to find /dev/sda. I know for a fact (from live USB use) that the SSD disk on this PC is indeed /dev/sda. But I think it needs some kind of a module to find it at boot.

Any ideas on how such a "loader USB stick" could be built? I assume it would need at least a bootloader like GRUB and possibly the Linux kernel, maybe even the initrd as well?


I am on the verge of changing the motherboard. At least Intel's own motherboards have a working BIOS and not this messy EFI stuff.

---

### Post by gordintoronto on 2011-12-16
Is the hard drive bigger than 2 GB? What video adapter?

---

### Post by oldfred on 2011-12-16
I do not have UEFI, but have saved some links of issues. Not sure if any are related. Are you sure you are in UEFI mode or BIOS mode?

Post this:
If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by zensov on 2011-12-16
Hi, I've been struggleling with an ssd drive issue the last couple of months.
I had my usual Kubuntu 32 bit on a sata drive and I wanted to give a try to Ubuntu 64bit on a new ssd 60gb disk.
The installation went well but after the first shutdown the nightmare started... 
It looks like the Bios of this Asus P5e3 mobo (wich I upgraded to the last version) does not handle properly the ssd disk which is correctly listed by the operating system as dev/sdb.
In the bios the ssd is not listed every time, it comes up only sometimes; and in any case it is never listed among the bootable devices (where you can set the priority).
So what happens is that Grub (which is installend in the old sata drive) does recognize the new ssd and /dev/sdb is listed among the Grub boot alternatives; BUT if I choose this one I get an error after a few second with blue screen: it says that /dev/sdb doesn't exist (!) or in other attempts that there's no kernel image ("you must load kernel first..."); and only sometimes it boots fine and the 64-bit Ubuntu system works very well running on the ssd disk...
A very big caos!
I can add that starting up is now very slow: I get a little dash lithening for a while when I start the pc, before getting the Grub display; everything went very fast when I only had the stata disk in the pc.
If I use ubuntu-boot-repair (I did more or less 50 times...) the ssd works fine at first reboot; after the first shutdown I get the same  mess...
Looks like something happens with the mbr of the ssd after the second reboot or at least the first shutdown.
Now I want to decide if it's better to go back to the only one os on the old sata disk or to remove the sata and try to use the new ssd alone (but I'm the problem should not be the cohabitation of those two drives rather the compatibility between the ssd disk and the mobo/bios).
Now I'll try to set the bios driver to raid, to see if something happens...

---

### Post by robgill on 2011-12-16
I currently us Asus P8H67 with EFI bios - 11.10 installed and boots without issue. 

I know it's silly but ensure the ssd is in the boot order.
Restore default bios setting or firmware upgrade. 

Sorry I do not have a great solution - just encouragement that 11.10 will work with asus EFI.

Good luck!

---

### Post by oldfred on 2011-12-16
Do not set to RAID in BIOS. That adds hidden parameters on a drive that prevent grub from working correctly.

I have a new SSD and boot with BIOS. I followed the advice and set it to gpt not MBR and it boots in less than 20 sec. After I added additional mounts and configuration it jumped to 25 sec to boot.

---

### Post by Ubutuxer on 2011-12-19
[B]SOLVED!
[/B]Some of the posts in this topic guided me in the right direction. I thank everyone who replied, including robgill for telling that it is possible to get Ubuntu 11.10 working with Asus EZ EFI. That kept me trying.


**SOLUTION**
1) GPT partitioning seemed to be a problem for the Ubuntu installer. I took the SSD disk out of the PC, plugged it to another PC with a SATA-to-USB adapter and created a normal partition table on it without any of the non-working GPT crap. I created the partitions as follows (with cfdisk, gparted also works):

1: FAT32 partition for the EFI bootloader. I set this to 500 MB size and formatted it with mkfs.vfat.
2: / (root) partition (ext4).
3: /home partition (ext4).

I use no swap on computers like this that have 16 - 32 GB of RAM.

2) I kept the SSD disk plugged to the other PC with the SATA-to-USB adapter and mounted the FAT16 EFI partition. I created a folder **efi/grub** under it with the command "mkdir -p efi/grub".

3) Now the disk was ready for installation. I put the SSD disk back to the new PC, booted up Ubuntu installation from the USB disk and installed it as usual, formatting / and /home as ext4 in the process.


**SUCCESS!!!**
The PC boots in about 10-15 seconds like you'd expect from an SSD disk. The network card on this motherboard works on Ubuntu 11.10 out-of-the-box as well. 10.04 doesn't seem to recognise it, 11.04 I'm not sure.


**My advice to others reading Ubuntu's EFI/UEFI instructions:**
[B]Do NOT start recompiling GRUB or other more complicated stuff. It is completely unnecessary.

The instructions are outdated for 11.10 and just creating the FAT partition with a folder efi/grub  is enough for Ubuntu to automatically recognise and install the bootloader there. Ubuntu 11.10 already has a working GRUB for EFI systems, you do NOT need to compile one yourself, at least not for the Asus EZ.[/B]


So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple. :guitar:

---

### Post by zuencap on 2012-01-18
This thread helped me a lot so I want to share my experience for others.

Differences in my case:
* P8H61MX Motherboard
* Linux Mint 12
* Sata HDD

I did these first but maybe they are unnecessary:
* Boot by usb live Mint
* Create a new gpt partition table by gparted. Created a 200MB fat32 partition at first. Set boot flag.
* Installed gdisk and checked made sure partition type is correct.
* Created efi/grub folder in the new partition.

then:
* Started installation
* In partition setup, set the first partition type as 'efi boot partition'.
* Set the same partition as 'boot loader installation partition' too.
* Created other partitions and continued.

---

### Post by dgoldssfo on 2012-02-04
I've been having an awful time trying to get 11.10 to work on a Lenovo ThinkServer TS130 with UEFI.

I finally came on an easy-to-do workaround - no messing with GRUB files or pulling hard drives out of cases - and am posting it here in case it might be of help to anyone. It takes a while but is simple to do.

1. Install 10.04 LTS. 
2. Upgrade to 10.10.
3. Upgrade to 11.04.
4. Upgrade to 11.10.

10.04 installs correctly on my system but the later releases do not. Once I get the base installation down, all the subsequent upgrades worked.

Strangely, my network adapter does not work with 10.04, so (rather than troubleshooting it) I downloaded the alternate CD for upgrading to 10.10. After I upgraded to 10.10, the network adapter started working and I was able to do the rest of the upgrades over the network.

I tried setting boot mode to legacy in my BIOS settings before installing but that did not work. The installer died after partitioning my drives.

In ten years of playing with Linux, I have never had such a bad installation experience, even in earlier days. SuSE 12.1 and Fedora 16 installers worked equally poorly. UEFI looks like a very bad thing for Linux users and the Linux vendors had better get their arms around it or desktop Linux is going to go away.

I think booting to a USB drive might be the best bet for this machine. I've never done it before, but think I might give it a try on this beast.

---

### Post by gordintoronto on 2012-02-04
The TS130 also has, "Enterprise-tough features like ECC memory, built-in RAID and 
latest Xeon performance," all of which are disruptive technologies.

The kernel included with 10.04 is probably why the wireless didn't work.

In a few months, people will be able to install 10.04, then upgrade to 12.04 in one step -- but it's a big step.

---

### Post by niglas on 2012-03-24
> **zuencap said:**
> This thread helped me a lot so I want to share my experience for others.

Differences in my case:
* P8H61MX Motherboard
* Linux Mint 12
* Sata HDD

I did these first but maybe they are unnecessary:
* Boot by usb live Mint
* Create a new gpt partition table by gparted. Created a 200MB fat32 partition at first. Set boot flag.
* Installed gdisk and checked made sure partition type is correct.
* Created efi/grub folder in the new partition.

then:
* Started installation
* In partition setup, set the first partition type as 'efi boot partition'.
* Set the same partition as 'boot loader installation partition' too.
* Created other partitions and continued.


Tried to follow you steps, but I cannot find the partition type "efi boot partition" (only ext3, ext4, fat32, etc), Where do I find it?

HW:

[LIST]
[*]Asus P8Z68-V
[*]OCZ Agility 3 Series SATA III 2.5" SSD 60GB
[/LIST]
[IMG]http://i.imgur.com/xOqpK.png[/IMG]

[IMG]http://i.imgur.com/rJDy9.png[/IMG]

---

### Post by jruden on 2012-04-01
> **niglas said:**
> Tried to follow you steps, but I cannot find the partition type "efi boot partition" (only ext3, ext4, fat32, etc), Where do I find it?
I wonder that to!

---

### Post by oldfred on 2012-04-01
If you are using gparted it is just click on partition and right click set boot flag.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

In gdisk, you'd give it a type code of EF00.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by niglas on 2012-04-14
I finally managed to boot with EFI, I wrote a guide of how I did it:
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

