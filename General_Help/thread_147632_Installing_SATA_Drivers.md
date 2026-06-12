---
title: "Installing SATA Drivers"
date: 2006-03-20
forum: General Help
---

### Post by moleman5 on 2006-03-20
Hi all,

I am trying to install SATA drivers which I have downloaded from ULi.  To cut a long story short I couldn't get either the Live CD or Install to boot on my system and figured out that it was connected to my SATA controller - I installed an old IDE drive which I had lying about (as you do!), disabled the SATA controller in the BIOS and Bob's you Uncle, etc.

I have done a full install of Breezy, installed Nvidia drivers and few other bits and pieces but I can't figure out how to install the SATA drivers and am in need of some guidance on how to do it, or an alternative workaround.

Below is a bit of the Read me with with zip I downloaded . . .,

1. M5288 SATA AHCI Driver(kernel 2.6.11 or later version kernel)



==================================================================

Using the linux kernel default m5288 SATA driver ahci.c

if your kernel image not include the ULi m5288 SATA driver,please

add it into kernel as the following steps:



Step 1:

	Change directory to /usr/src/linux-2.6.x

	Run command  "make menuconfig" then 



	Select "Device Drivers"

	Select "SCSI Device Support"

        Select "SCSI low-level drivers"

	Select "Serial ATA(SATA) support" as "y"

        Select "AHCI SATA support" as "y"

	Before exit, save your configration.



Step 2:

	make

	cp arch/i386/boot/bzImage /boot



Step 3:

	If you use grub to boot your linux, then

	  1) Modify the file /etc/grub.conf by adding

		title 2.6.x

		root (hd0,2)

		kernel /boot/bzImage ro root=/dev/hda1

		The disk partition where your linux resides in, 

                for example: /dev/hda1

	  2) Reboot and select the kernel 2.6.x

Is this done in Terminal? When I change directory, the very first step, I am told that directory does not exist.  I have searched for the file in /usr/src/ but it is not there.  I have made myself a member of the src group but still nothing.

Any suggestions would be greatly appreciated.  I would like to enable the SATA contoller and use the bigger hdd installed.

Many thanks in anticipation

---

### Post by MRius on 2006-03-20
You need to get the kernel source first and uncompress it on /usr/src

---

### Post by rattking on 2006-03-20
Hi
ahci is already in the 2.6.12-10 kernel have your tried that?
sudo modprobe ahci
otherwise the only reasone to recompile the kernel would be if you changed the source.. because those options are already enabled

---

### Post by moleman5 on 2006-03-21
Thanks for the replies, I'll have a look at it again when I get home and let you know how I get on.

---

