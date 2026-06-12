---
title: "Help? is my computer bricked?"
date: 2010-06-06
forum: General Help
---

### Post by bhous3 on 2010-06-06
WOW guys! I am in deep doodoo here. 

So, I've been running 9.10 for a while and happy with it, no problems or anything. I recently purchased an iPhone, and wanted to run windows again--not single boot, dual boot, mind you! I got an installation disk and it told me it could not find a hard disk drive.

I then used gparted to create 2 partitions, but I messed it up because now if I want to boot, it sends me to grub recover and I have no clue what to do there. I tried to boot off of my live ubuntu disk, but after I select an option, the ubuntu logo is the only thing that appears on my screen, middle-left ish. nothing else.

I am downloading 10.4 right now, but will this help? All I want to do is dual boot!

---

### Post by #!/bin/bash on 2010-06-06
Probably the windows install disk messed up your MBR or the boot sector of your linux partition. Just creating 2 partitions is not going to fix the problem, you'll need to either fix the linux installation or do a complete reinstall. As for the windows install you'll need to create a ntfs partition once you fix your ubuntu. Another option would be virtualbox. I use vbox with my iPod touch and it works fine, maybe it will work with iphone too.

---

### Post by rizzeh on 2010-06-06
easier way to do dual boot is to install windows first, then linux. 
 Use MSDOS fdisk tool to restore MRB,  Boot with windows startup floppy or CD and run:
```
fdisk /mbr
```

---

### Post by bhous3 on 2010-06-06
so my first step is completely reinstalling ubuntu-- check. I could try virtualbox, but I'm not so sure how well it will work for what I want to do. How should I partition my hard drive once I install 10.04?

---

### Post by bhous3 on 2010-06-06
> **rizzeh said:**
> easier way to do dual boot is to install windows first, then linux. 
 Use MSDOS fdisk tool to restore MRB,  Boot with windows startup floppy or CD and run:
```
fdisk /mbr
```
the problem is windows can't find my hard drive, I know I messed it up but I don't know how.

---

### Post by Leppie on 2010-06-06
what version of windows did you order/receive?

you most probably can restore grub2 easily using the lucid livecd.
you will have to know which partition is the karmic system partition.
in the lucid live environment pull up a terminal and issue the following command:
```
sudo fdisk -l
```
check the partitions and take note of your karmic system partition (of course you can skip this step if you already know which one that is). you will need to mount that system partition. for now i will assume that your karmic system partition is /dev/sda5 (amend this wherever you see this reference).
issue the following commands:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
reboot

---

### Post by 4Orbs on 2010-06-06
Do you have any other partitions on the hdd for storage of media or important files that you are trying to save? If not, and you want to start over from a clean hard drive... this is what I would do if this were my computer:
1. Boot the Ubuntu live cd and select "Try without changing anything" and once you get to the desktop of the live cd, open the System>> Administration>> Partition Manager(gparted)
2. When gparted is open, delete the existing partitions and click the "apply" button.
3. At the top of gparted click on "Device" and click "create partition table" and select msdos as the format.
4. Create the first partition for Windows. Whatever size you wish and format as ntfs. Make sure this is a primary partition, not a logical partition. Turn "On" the bootflag for this partition.
5. Create the second partition for Ubuntu root (/)... Make it about 10 to 20 gb and format to ext4. This can be either a primary or logical partition but I recommend a primary unless you intend to have an extra storage partition on the hard drive. Don't install Ubuntu, just create the partitions without assigning the mount point.
6. Create the third partition for Ubuntu /home and use all remaining unallocated space on the hard drive minus whatever you will need for swap (twice the size of your ram). Format as ext4. Make it the same as your root partition (either primary or logical). Don't install Ubuntu. Just create the partition without assigning the mount point.
7. Create the final partition as swap using the remaining unallocated space (twice your ram size). Don't install Ubuntu. Just create the partition.
8. Apply all pending actions in gparted. Then close gparted and exit the Ubuntu live cd.
9. Boot into the Windows install disk and it should now find your hdd. Tell it to do a quick format of the first partition as ntfs. Install Windows. When the Windows installation reboots, keep the disk in the tray because it may not be finished installing... this happens with some.. versions.
10. After Windows finishes installing, boot back into Windows just to be certain it works.
11. Exit Windows and install Ubuntu. When you come to the partitioning portion of Ubuntu install, select "Manual" partitioning option and specify the proper mount points on your already-existing partitions.
12. Everything should work perfectly when finished.

---

