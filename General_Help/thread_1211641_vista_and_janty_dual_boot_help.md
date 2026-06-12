---
title: "vista and janty dual boot help"
date: 2009-07-12
forum: General Help
---

### Post by ducks on 2009-07-12
ok so i am trying to dual boot ubuntu and vista and i am not using different partitions but different harddrives all together and so i installed ubuntu on my other hard drive that didnt have vista and now when i boot my computer it starts to load grub but then i get the grub 17 error now i have tryed to reinstall grub with the dd commands and that didnt work so i formatted the drive that ubuntu was on thinking that it would get rid of grub completely but it didnt and i have tryed to use the vista recovery disk but that comes up with some error and does load properly i dont think. so right now i have ubuntu install on sdc and vista on sda but when i installed ubuntu again i didnt install the bootloader with it this time and that is were i am at now, does anyone have any ideas of how to fix it?

---

### Post by mano cazalet on 2009-07-12
foud this guide for you:
[Dual Boot Ubuntu / Windows (2 Drives)]("http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives#Short%20tutorial")

---

### Post by anystupidname on 2009-07-12
Boot from a liveCD or liveUSB and lets see the output for:
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb
sudo fdisk -l /dev/sdc

Lets see also /boot/grub/menu.lst from whatever drive grub is installed on.

I suspect you'll need to follow steps something like these from your liveCD:

> sudo grub
find /boot/grub/stage1  #you will get a response such as root (hd0,2)
root (hd0,2)    #use the numbers from the previous command
setup (hd0)
quit

---

### Post by lindsay7 on 2009-07-12
Type these commands in the terminal and post the results here, these will tell us what is going on with your computer

sudo fdisk -l  that is the small case letter L

cat /boot/grub/menu.lst

cat /etc/fstab

---

### Post by ducks on 2009-07-12
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d1d5d1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x068b068b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris

```

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc5 swap swap defaults 0 0
```

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0a5315bc-f6f1-4890-a73e-b12ce372f07b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0a5315bc-f6f1-4890-a73e-b12ce372f07b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0a5315bc-f6f1-4890-a73e-b12ce372f07b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0a5315bc-f6f1-4890-a73e-b12ce372f07b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0a5315bc-f6f1-4890-a73e-b12ce372f07b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by lindsay7 on 2009-07-12
try this

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by ducks on 2009-07-12
still gives me the grub error 17

---

### Post by lindsay7 on 2009-07-12
Go into your bios settings and make sure that you are booting from the hard drive sda where windows is installed.  It will be listed in the bios as boot priority for the hard drives.

---

### Post by ducks on 2009-07-12
now after changing that so that windows has the first priority i get the grub error 25

---

### Post by lindsay7 on 2009-07-12
Ok, I think you need to add two map lines to your grub menu

Type sudo gedit /boot/grub/menu.lst in the terminal and add the lines in red


```
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
[COLOR="Red"]map             (hd0) (hd2)
map             (hd2) (hd0)[/COLOR]
chainloader	+1
```

save the file and close the file and reboot.

---

### Post by ducks on 2009-07-13
after adding the lines i still get error 25 when windows drive is first on priority and when the linux drive is first i get error 17

---

### Post by lindsay7 on 2009-07-13
Well, there is something here that I am missing.

You may want to download Super Grub and run it. You can reinstall the mbr to the Windows partition and reset the grub menu for a multiboot system.

[http://developer.berlios.de/project/showfiles.php?group_id=10921](http://developer.berlios.de/project/showfiles.php?group_id=10921)

or

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

You want the iso file for Linux

---

### Post by ducks on 2009-07-13
tryed that and it gives me some cant read partition error and then just ends up at a:\ and i dont know what commands to use

---

### Post by lindsay7 on 2009-07-13
These are web sites you copy them into the http address bar on your browser, i.e Firefox or Opera or whatever you use.  Download the SuperGrub ISO file and burn it to a cd. Use this disk to boot the computer.

---

### Post by ducks on 2009-07-13
i burned the disc but when it trys to boot from it, there is an error that it cant read some partition table and does that a few times then it just got to a command prompt a:\

---

### Post by lindsay7 on 2009-07-13
I am going to call it a night, If you want to get Vista back and work on the dual boot later.  Here is what you can do if you have the Vista Install disk with you.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you do not have the Vista disk, you can download a recovery disk here,

[http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)

---

### Post by lindsay7 on 2009-07-13
You need to burn it as an ISO image.

---

### Post by ducks on 2009-07-13
thanks for the help the burning program on this laptop is retarded and so i had to burn it with alcohol 120 and got it working now

---

### Post by anystupidname on 2009-07-13
@duck: Let us know if you'd like to try to get dual boot working again. Are you drives SATA or EIDE?

For the grub error 17 see [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
For the grub error 25 should mean the menu.lst has in invalid line

The fact that SuperGrub gave an error about reading partition tables would tend to make me think there is a drive geometry problem either caused by wrong BIOS settings for the drive(s) and/or a damaged disk controller and/or some sort of DDO (dynamic drive overlay)...

---

### Post by lindsay7 on 2009-07-13
> **anystupidname said:**
> @duck: Let us know if you'd like to try to get dual boot working again. Are you drives SATA or EIDE?

For the grub error 17 see [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
For the grub error 25 should mean the menu.lst has in invalid line

The fact that SuperGrub gave an error about reading partition tables would tend to make me think there is a drive geometry problem either caused by wrong BIOS settings for the drive(s) and/or a damaged disk controller and/or some sort of DDO (dynamic drive overlay)...


I think you are on to this after I looked at the results of the cat /ect/fstab

Testdisk may be worth running here,  see this link

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by ducks on 2009-07-13
that error with super grub was cause i used some dumb burning program to burn the cd for it but i did it with alochol 120 and it work perfect and i am still trying to get the dual boot working i am trying to use easybcd and neogrub but when i select ubuntu it still gives me the error 17

---

