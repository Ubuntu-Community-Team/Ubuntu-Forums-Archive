---
title: "Windows 98"
date: 2010-08-22
forum: General Help
---

### Post by xDonny on 2010-08-22
I want to put Windows 98 on my laptop, i'm running ubuntu 9.04. How can I do this from WITHIN ubuntu? I have PLop and I can boot it from grub to access my usb device, and I have a windows98se iso. Any suggestions? This computer does not have a cd/floppy drive so i have to boot from USB via PLop as my bios does not support it. thanks.

---

### Post by xDonny on 2010-08-22
can nobody help me? i really need to figure this out

---

### Post by ubun_two on 2010-08-22
Install it inside VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by xDonny on 2010-08-22
I want to install winows 98 OVER ubuntu

---

### Post by Ginsu543 on 2010-08-22
So do you want to keep Ubuntu (run Windows 98 alongside Ubuntu as a dual-boot or virtual machine), or do you want to get rid of Ubuntu and run Windows 98 exclusively? If it's the former, you'll have to decide whether you want to dual-boot or run it in virtual machine (each has different steps to take), but if it's the latter, just pop the Windows 98 CD into the CD-ROM, boot from the CD, and follow the directions in the install process to format the partition you're installing it into. There is no way to install Windows 98 over Ubuntu from inside Ubuntu.

---

### Post by xDonny on 2010-08-24
Please read, i have no cd drive or floppy drive, and i want to dual boot, how can i do this from grub2? i have the iso file.

---

### Post by Ginsu543 on 2010-08-24
I don't think Windows 98 can be installed without a CD drive because the installer itself expects its install files to be located on the install CD and looks for one while it runs.

The only other option I can think of is to try using UNetbootin to create a bootable USB thumbdrive using the Windows 98 iso and run the installer off the USB drive. But if my memory serves me correctly, the Windows 98 installer is very picky about where its files are located.

---

### Post by xDonny on 2010-08-24
alright is there anyway i can make another partition and put windows xp setup files on there and have it run?

---

### Post by jocko on 2010-08-24
Is there any way you can boot a windows 98 boot disk (I guess any other dos boot disk would work too) from a usb device instead of from a floppy? I'm pretty sure it should be possible, google for it.
In that case I think you should be able to install windows 98 by a few simple steps (can't be very specific, I haven't seen windows 98 in more than ten years):
1. Make two fat32 partitions. The first one will be the windows "c:\" drive and needs to be the first partition on the hard drive, as this is the only way windows 98 can boot. The other one will be used for the installation files.
2. Copy all the windows 98 installer files from the iso (you can mount it in ubuntu, if you don't know how just google for it) to the second partition.
3. Boot from the windows 98 boot disk.
Now you should be able to install windows. I don't remember the exact steps, but I think this command should start the installer (before you start, make sure you find this file):
```
d:\setup.exe
```
If the installer asks where the files are, they should be in a directory which I think should be named "d:\i386" or something similar...

---

### Post by Kranix on 2010-08-24
Why do you want to install windows 98 anyway?

---

### Post by lisati on 2010-08-24
I'm inclined to agree with Jocko's suggestion. It has been a while since I've had Win98SE on any of my machines, but the basic idea seems sound.

---

