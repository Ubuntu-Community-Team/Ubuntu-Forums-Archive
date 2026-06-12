---
title: "What does USB Statup Creator really do?"
date: 2012-03-19
forum: General Help
---

### Post by torvald on 2012-03-19
I'm trying to make a USB pen bootable after mixing a Ubuntu distro with remastersys using only bashscript for the porpuse of batching it up later on.

So I made a Ubuntu pen with USB Statup Creator and backed the first 512B of the USB with dd to get the partiotiontable and the MBR. Then I dd'd this to a new fresh USB stick of the same vendor and copied all the files on the USB stick made by USB Statup Creator to the new stick.

The USB Statup Creator stick boots like a sharm both on EFI and BIOS, but the one that I've copied dose only boot on EFI bot no BIOS. The both look exactly the same in fdisk and the md5 over all the files on both sticks are identical.

What am I missing? Any links to the "secret of bootable USB sticks" or advice is appreciated. :)

---

### Post by forestG on 2012-03-19
Maybe there are some .* files that you have not copied. 

I suspect (without being certain) that when you make a bootable disc you create also a boot sector. These data are not really related to some OS (Linux,Windows,etc) but they "speak" directly to the hardware to help the computer load the rest of the data from the hard disk. 

Imagine a computer starting, the computer cannot know where to look for the data, it is not aware of the operating system on the hard disk or anything else. The only "program" loaded is the BIOS. Therefore what is needed is a standard "place" in the hard disk or the flash disk (maybe certain addresses) which is called the boot sector where the computer reads first in order to be guided and load the rest of the data. 

Since you have copied the files inside an operating system it is possible that the data which are not OS-dependent are not copied. 

That is why you need a special boot-disc creator for every usb-stick.

EFI is much more modern and more advanced and it has different architecture. I do not know much about it.

---

### Post by Ghost_Mazal on 2012-03-19
Also , the UUID's of the disks will be different. Both grub and fstab will be confused.

I am not clear what exactly you are trying to do. Do you want to put your remastersys iso onto a USB stick ?

Or your whole system onto the USB stick ?

If the first , simply use unetbootin to transfer the iso to USB stick.

---

### Post by torvald on 2012-03-19
I looks like we got it to work by using an MBR which we found in the syslinux package: /usr/lib/syslinux/mbr.bin. Just dd'd that one onto first 446B of the USB stick.

We are making a customized Ubuntu live distro which will be used on exams to offer a secure enviroment (no internet, only whitelisted software allowd) for the students at our school. Now we are making bash-script so the modifyed USB sticks can be made easy by a teacher. :)

Allthough the answare wasn't fully solved I closed it since we found a fix.

---

