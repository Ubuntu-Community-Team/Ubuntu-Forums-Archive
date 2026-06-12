---
title: "Corrupted system :( need urgent help.."
date: 2011-03-21
forum: General Help
---

### Post by unreademail on 2011-03-21
Hi guys,

well at the moment I'm currently in distress because my  Ubuntu system that has my university assignment doesn't work. Not only that, when I tried to fix it I managed corrupt the dual boot I had and now cannot login into either Windows 7 or Ubuntu (besides the USB tryout version which I'm currently on now).

Please help me.

I'll try and describe what happened in the beginning.  I was rushing to get to class so I needed to shut down my Ubuntu  system quickly. The quickest way was  to obviously hold down the off  button however later when I got home to finish off my uni assignment I  couldn't boot into linux! I just get a dos command line with the word grub on it..

Next I tried fixing it using the method found here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

However not only did it not fix my problem I now can't boot into anything except from this Ubuntu Live CD.

D:

edit: I'm using Gnome Ubuntu 10.10 Desktop

---

### Post by BbUiDgZ on 2011-03-21
> **unreademail said:**
> Hi guys,

well at the moment I'm currently in distress because my  Ubuntu system that has my university assignment doesn't work. Not only that, when I tried to fix it I managed corrupt the dual boot I had and now cannot login into either Windows 7 or Ubuntu (besides the USB tryout version which I'm currently on now).

Please help me.

I'll try and describe what happened in the beginning.  I was rushing to get to class so I needed to shut down my Ubuntu  system quickly. The quickest way was  to obviously hold down the off  button however later when I got home to finish off my uni assignment I  couldn't boot into linux! I just get a dos command line with the word grub on it..

Next I tried fixing it using the method found here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

However not only did it not fix my problem I now can't boot into anything except from this Ubuntu Live CD.

D:

edit: I'm using Gnome Ubuntu 10.10 Desktop

first thing you should do is use the live cd to recover your data: copy it to a network location or usb drve.

then [fix your windows 7](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems) bootloader.

then reinstall grub ;)

---

### Post by bleedingsamurai on 2011-03-21
to add to what BbUiDgZ said, once you reinstall grub (which you can do from the LiveCD) you will also need to run fsck from the LiveCD. you'll need to find out what partition your home/root directory is on and run run:
```
sudo fsck -r /dev/partition_here
```
the -r option will fix stuff but will ask for your confirmation, just in case you see something you don't want to fix.

---

### Post by BbUiDgZ on 2011-03-22
> **bleedingsamurai said:**
> to add to what BbUiDgZ said, once you reinstall grub (which you can do from the LiveCD) you will also need to run fsck from the LiveCD. you'll need to find out what partition your home/root directory is on and run run:
```
sudo fsck -r /dev/partition_here
```
the -r option will fix stuff but will ask for your confirmation, just in case you see something you don't want to fix.
you may even have to do this first before you can recover your data

---

### Post by dragonfly41 on 2011-03-22
Can fsck be used on an NTFS partition (holding both Vista and Ubuntu windows installation)?

ubuntu@ubuntu:~$ sudo fsck -r /dev/sda3
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda3


Ubuntu is used in demo mode - not full installation - until I can recover windows files (Vista will not boot up the whole way from that partition and stalls after loading windows drivers in safe mode).

---

### Post by Mark Phelps on 2011-03-22
> **dragonfly41 said:**
> Can fsck be used on an NTFS partition (holding both Vista and Ubuntu windows installation)?

You should use CHKDSK on NTFS partitions, not fsck.  However, since the Ubuntu install is basically one big file, it's likely that chkdsk will not do anything with it.

---

### Post by cipherboy_loc on 2011-03-22
To mount the big file, follow the directions on how to migrate from Wubi to a new installation.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

DO NOT RUN CHKDSK, it has a habit of deleting stuff.


Cipherboy

---

