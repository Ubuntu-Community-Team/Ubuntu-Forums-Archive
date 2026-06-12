---
title: "BIOS to UEFI possibe with 10.04 LTS?"
date: 2011-04-27
forum: General Help
---

### Post by alphaamanitin on 2011-04-27
Hey guys,

I have a UEFI MOBO and I *cannot* get 11.04.2 beta2 AMD64 to install.  Everytime it hangs at the GRUB2 install and the install breaks with /target created.  Anyway, is it possible to install 10.04 AMD64 LTS as bios, boot into it and then edit the front partitions to make the needed UEFI partitions, install GRUB2 and manually build the UEFI boot files necessary for UEFI booting?  If so, can some one help me out with the most likely path to follow?

Am comfortable editing partitions in GParted and Disk Utility, using command line, and can follow directions well.  Am not concerned about data on the disk so this can be done as many times as necessary.  

Thanks AlphaA

---

### Post by dino99 on 2011-04-27
[http://www.chromeoslounge.com/cr-48-chrome-notebook/1709-ubuntu-11-04-alpha-3-cr-48-uefi-booting.html](http://www.chromeoslounge.com/cr-48-chrome-notebook/1709-ubuntu-11-04-alpha-3-cr-48-uefi-booting.html)

and more info following the link below

---

### Post by alphaamanitin on 2011-04-27
Which link?  I have read that chromeoslounge and I do not think it is particularly helpful.  Also, my problem is that Ubuntu 11 that supports UEFI booting will not install correctly period. The install in that thread works, mine breaks at the GRUB2 install.  

I am specifically asking for steps necessary to convert 10.04 LTS GRUB2 to GRUB2 with efi booting, and get it working.

AlphaA

---

### Post by srs5694 on 2011-04-27
My suspicion is that you're running into problems because of an incorrect type code on the EFI System Partition (ESP) in your hard disk. Please boot with [Parted Magic](http://partedmagic.com) and type the following command:

```

sudo parted -l

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] blocks. I recommend you do this because the alternative you suggest, although possible, could run into another layer of problems. If you insist on trying, the procedure would be, in outline:


[list=1]
[*]Set the computer to boot in BIOS mode.
[*]Boot some utility (perhaps the Ubuntu installer, or some other recovery disc) and create several partitions: A [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) (~1MiB, no filesystem), an [EFI System Partition](http://en.wikipedia.org/wiki/EFI_System_partition) (~100-200MiB, FAT32), and whatever partitions you want for Linux. You *must* set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-2TB disks, so you may need to use another utility to do the partitioning.
[*]Install Ubuntu normally.
[*]Test that Ubuntu boots and works.
[*]Read, understand, and follow the procedure on [the Testing on UEFI page.](http://grub.enbug.org/TestingOnUEFI) It describes how to set up GRUB using (U)EFI mode by compiling the software from source. (If you're having problems installing Ubuntu's GRUB in (U)EFI mode, you're likely to be better off installing it this way. Note this means you may need to manually update your GRUB configuration whenever you install a new kernel.)
[*]Shut down and reconfigure the computer to boot in UEFI mode.
[*]Hope it works.
[/list]


Another alternative may be to try your already mostly-installed Ubuntu system. Boot the install disc into "live CD" mode and then follow the directions [here](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/) (steps 1-6) to get access to your just-installed system. You should then be able to install GRUB from source, as described on the [Testing on UEFI](http://grub.enbug.org/TestingOnUEFI) page.

---

### Post by alphaamanitin on 2011-04-28
Have given up on Ubuntu for now.  Downloaded daily build last night, it installed, who knows if it was in UEFI mode though.  I know ```
dmesg | grep EFI
``` showed that the liveCD was at least running in UEFI mode, but as for the install?  It did make it past grub this time, and indicated it was installing grub-efi.  However, restarting the computer=no boot.  Not even grub rescue, MOBO reported back no operating system on that disk.  I let the computer erase and use the entire drive as well.  I'm done wasting my time until Ubuntu is better tested in UEFI.  

I think I'll save up and buy another SSD to boot Ubuntu from a separate drive anyway, I don't really like booting from the same drive.  Windows 7 x64 boots perfectly in UEFI mode, lol.  Usually I have more stability problems with Windows than Ubuntu.  Also, I really HATE unity and want to use an LTS release.  I think I'll look around to see if anyone modifies 10.04 LTS to boot uefi or figure out how to change 10.04 to UEFI capable.  

Thanks for all the help guys.  Instead of solved we need a marker like, not solved but dead.

AlphaA

PS-the GRUB testing on UEFI is a dead link.

---

### Post by oldfred on 2011-04-28
I cannot find any recent bugs in grub posted on efi.

You should add a bug and either they will suggest something that already is solved, a work around or add it to the list of official bugs. Otherwise fixes for your case may not happen soon.

You do have to create a new account &  login to post a new bug.
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

### Post by alphaamanitin on 2011-04-29
Yeah, I keep meaning do report a bug and then keep getting busy at work or working on the computer.  Right now I cannot continue testing either.  I think I will buy a 128gb SSD because windows7 ultimate is taking up basically all of the 64gb drive I have.  Then I will clone windows to the 128 and install ubuntu on the 64 cause ubuntu needs lots less.

AlphaA

---

