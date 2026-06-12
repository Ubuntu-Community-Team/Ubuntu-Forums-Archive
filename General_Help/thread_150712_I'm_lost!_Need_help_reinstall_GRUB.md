---
title: "I'm lost! Need help reinstall GRUB"
date: 2006-03-26
forum: General Help
---

### Post by gman2004 on 2006-03-26
Sorry guys but I have read almost every thread, but it seems I can't get that GRUB running.
I started with LiveCD, I did sudo fdisk -l, with the following results:
> root@ubuntu:~# sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19929   159830685    5  Extended
/dev/hdb5              32       19929   159830653+  8e  Linux LVM

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        4863    39062016    7  HPFS/NTFS
/dev/hde2            4864        9728    39078112+   f  W95 Ext'd (LBA)
/dev/hde5            4864        9728    39078081    7  HPFS/NTFS

Disk /dev/hdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       14592   117210208+   7  HPFS/NTFS
root@ubuntu:~#

I tryed to go through tty, but I could not figure out which one is the boot partition.
I tryed sudo -i, but it didn't ask for password, is this normal? I typed "grub" and then "find /boot/grub/stage1" and get "Error 15: File not found"
I used "Super Grub Disk" no luck either.
I used instrallCD but when it came to partioning, I couldn't get to the right partition.
I don't to want to reinstall Ubuntu, I have files that I want to keep on the drive.
Any suggestions, are more than welcomed.

---

### Post by arnieboy on 2006-03-26
[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

---

### Post by gman2004 on 2006-03-26
I followed the link, but I get stack at the partion creation.
At the drive where I installed Ubuntu, I see two partitions:
#1 primary 255MB ext3 mounted at: /media/hdb1
#5 logical  163GB  lvm  not mounted.
I do not see a swap partition
I select #1 primary partition and mount it as /. I presss enter at fifnish partition, but nothing happens, it comes back to the same screen. If I "go back" it takes me back to partion menu.

---

### Post by gman2004 on 2006-03-31
I guess I have to quit bothering with Ubuntu.
Either I'm stupid and I do not understand what people are telling me 
or the help is not there as I wanted to believe.

---

### Post by justleen on 2006-03-31
[QUOTE=gman2004]I guess I have to quit bothering with Ubuntu.
Either I'm stupid and I do not understand what people are telling me 
or the help is not there as I wanted to believe.[/QUOTE]
\

now now.. not so down :)


what worked for me, was to boot from the ubuntu CD, type RESCUE at the prompt.
Once finished loading, just type GRUB-INSTALL ..
BUT! this wil just overwrite your MBR on the first drive.. might nog be the safest :)   (i dont know what your "start sitution" was

The options that Arnieboy posted should do the trick for ya
By the looks of the fdisk -l the main linux is /dev/hdb1
you're right that you dont have a swap, im guessing you manually partitioned, and didnt create one?

as far as the problem of the setup that doenst continue.. im not sure whats going there.. Sure your not missing sometyhing on that screen? Write partition and finish.. something like that..

Its not an option to start over? gives you a chance to create some swap space as well

---

### Post by gman2004 on 2006-04-04
Thank you for your support, but I still can not recover grub.
I will try some other time. 
You see I do not want to overwright the drive. I do not want
to loose the data. I was loosing the drive and I backed up 
everything to the Ubuntu drive.
Is it possible I have a bad install CD? I'm trying to install 
Ubuntu on my other computer but I can do that either!
I have posted three times, with no solution yet! and very
minimal responce.
I will try one more time if it doesn't work, I guess Bill is going
to be my friend for life:cry: :cry: :cry:

---

### Post by gman2004 on 2006-04-05
Update:
I did rescue and from shell I typed "grub", I got the following error: "Probing device to guess BIOS drives. Error opening Terminal: bterm"
I triyed "grub-install /dev/hdb1" and I get:
"/dev/mapper/Ubuntu-root does not have any corresponding BIOS drive"
I guess there is something missing?

---

### Post by arnieboy on 2006-04-05
I think your installation is grossly screwed up and you should not waste so much  time trying to correct it with your minimal linux knowhow.
Try this instead:
get hold of a live Ubuntu/Knoppix CD. Boot into that. Copy all your backed up windows data on to an external hard drive/thumb drive.
Reinstall Ubuntu.

also make sure by doing a md5 checksum that your install CD is not screwed up.

---

### Post by gman2004 on 2006-04-05
Can I install Ubuntu on an other drive? Will I be able to see the existing Ubuntu drive and back up what I need?

---

### Post by arnieboy on 2006-04-05
[QUOTE=gman2004]Can I install Ubuntu on an other drive? Will I be able to see the existing Ubuntu drive and back up what I need?[/QUOTE]
yes u can.

---

### Post by gman2004 on 2006-04-05
Thank you.
I will try and keep you posted.

---

### Post by gman2004 on 2006-04-11
All these started because I had to install windows and I could not install Grub. So I installed Ubuntu on an other drive (hde). I'm trying to recover data from an other drive (hdb)that I had install ubuntu before. These is the drives Ubuntu sees on my system.
> Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19929   159830685    5  Extended
/dev/hdb5              32       19929   159830653+  8e  Linux LVM

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9351    75111876   83  Linux
/dev/hde2            9352        9729     3036285    5  Extended
/dev/hde5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       14592   117210208+   7  HPFS/NTFS

The ststem lets me mount the hdb1 partitions to /media but it will not let me mount the hb2.
I did System/ Administrator/ Disks/ Hard Disk/ Partitions/ Access Path /media/hdb2, but when I click enable nothing happens.
Also at Partition Properties I see the followings:
Device:   /dev/hdb5
Filesystem: Unformatted!!!!!!!!!
Access Path: /media/hdb2
Size: 142.53GB Free space not available!!!!!!!!!!
Status: Inaccassable

When I boot Ubuntu I get the error that hdb1 can not be mounted and check the dmesg to see the error log (Quote below)
> [4294675.677000] hde: WDC WD800BB-00CAA1, ATA DISK drive
[4294675.997000] hde: cache flushes not supported
[4294675.997000]  /dev/ide/host2/bus0/target0/lun0: p1 p2 < p5 >

I did sudo mount /dev/hdb5 /mnt and I get the error "mount: you must specify the filesystem type
"
I guess I need help!
Thank you one more time!

---

