---
title: "Ubuntu 9.10 boot problems"
date: 2010-04-14
forum: General Help
---

### Post by frankvetter on 2010-04-14
I recently installed Ubuntu 9.10 on a PC - deleted Windows so no dual boot issues. It works great for the application I'm using it for, solid as a rock, but if I ever have to reboot it's a battle. Boots from GRUB - I neglected to create a boot diskette on install and would like to create one now but all the writeups I see on boot disk creation mention files that don't exist in /boot/grub. Is there a better way to boot Ubuntu? Write to MBR & bypass GRUB altogether - again, no windows dual-boot.
 
Sure could use some help on this one - Ubuntu is a great product with a big weakness.

---

### Post by agnes on 2010-04-14
What is the problem with Grub exactly? That Grub is taking too long to start?

> all the writeups I see on boot disk creation mention files that don't exist in /boot/grub
Because Ubuntu 9.10 has replaced Grub 0.97 or so with Grub 2 (beta).
Grub 2 is different from previous releases, for example has no menu.lst, instead it has a grub.cfg. 

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")(long)
[How to downgrade Grub to the below 2 version]("http://brettshaffer.com/blog/linux/downgrade-grub-2/") (so you can apply the writeups)

I' ve heard mentioned by some people Grub 2 is slower than the versions before.

---

### Post by mk1w86 on 2010-04-14
Grub is necessary to boot Ubuntu, so you cannot bypass it as you suggested.  I'm not 100% sure what your current setup is but Grub normally gets wrote to the MBR when you install Ubuntu. :confused:

To install Grub to the MBR run:

```
sudo update-grub
```

and 

```
sudo grub-install [your hard drive*]
```

*probably /dev/sda if you only have a single drive, if in doubt run:

```
sudo fdisk -l
```

to list all your drives and partitions.

For more information on Grub have a look here:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

The problems you were having with the guides on creating a boot disk are probably because Ubuntu 9.10 uses Grub2 by default which is fairly new so many guides are for the now legacy Grub 0.97 and earlier. ;)

---

### Post by quadproc on 2010-04-14
> **frankvetter said:**
> I recently installed Ubuntu 9.10 on a PC - deleted Windows so no dual boot issues. It works great for the application I'm using it for, solid as a rock, but if I ever have to reboot it's a battle. Boots from GRUB - I neglected to create a boot diskette on install and would like to create one now but all the writeups I see on boot disk creation mention files that don't exist in /boot/grub. Is there a better way to boot Ubuntu? Write to MBR & bypass GRUB altogether - again, no windows dual-boot.
 
I do not know what kind of problems you are having with the boot process so I can't suggest anything for that, but I can suggest a fairly easy way to create a bootable USB flash drive: use the Ubuntu USB Startup Disk Creator.  You'll need a big enough USB drive and the .iso file for the version of Ubuntu that you want.  Depending on what is already on the USB drive, you may need to use Gparted to clean it out.  Otherwise the process is straightforward.

I do not think that it would be wise to go straight to the kernel and avoid grub - that would be a lot of work, and it would prevent you from being able to use recovery mode, memtest, or anything else that you might want from a portable boot device.

quadproc

---

### Post by WinterRain on 2010-04-14
You can't get rid of grub, as it is necessary to boot into ubuntu. But you can reinstall grub or edit your grub file. With only ubuntu on the machine, it will load grub without you seeing it. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Btw, that is not a weakness in ubuntu, you just need to know what to do. Linux is not windows.

---

### Post by frankvetter on 2010-04-19
The problem I have with GRUB (now I know it's GRUB2) is that it starts to boot, then accesses the floppy drive (there's nothing in the FDD) and locks up - FDD light stays on & system hangs.

---

### Post by ed-koala on 2010-04-19
Check your BIOS boot order.  Make sure the FDD isn't before the hard disk.

---

### Post by frankvetter on 2010-04-19
Check your BIOS boot order. Make sure the FDD isn't before the hard disk
 
It's not - I even tried disabling the fdd in bios, the only difference there is that it doesn't turn on the fdd led.  I've been reading the writeup on GRUB2 & it mentions a problem (not defined in the writeup) with the --no-floppy entry in grub.cfg & suggests editing grub.cfg to remove all entries of "--no-floppy".  I'll do some more checking on this as I'd rather not directly edit grub.cfg but that may have something to do with my problem.

---

