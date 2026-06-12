---
title: "Formatting removable media"
date: 2009-07-03
forum: General Help
---

### Post by Toriam on 2009-07-03
During the install of Xubuntu to my netbook, I made a few oopsies and rendered 2 flash drives and an sd card near useless. They have the Xubuntu install media on them now, which I can't remove, the title of the card/drive is now 'Xubuntu 9.04' and I can't change the permissions to write or erase the info on the device. I was using unetbootin and ubuntu imagewriter to write to the drives. I tried to reformat using gparted and gnome format, with no luck, i unmounted the drive first. I'm about at a stopping point since I can't figure out where to go next. I'm not too terribly good at terminal so if you make suggestions along that line please be specific. 
Beth

---

### Post by geirha on 2009-07-03
First off, find the correct device node name of the external drive in question. You can identify it with gparted, I'll assume it's /dev/sdb, replace it with the correct one in all of the commands below

Make sure the drive is not in use; unmount if necessary.

Run the following in a terminal
```
sudo fdisk /dev/sdb
```

This will get you a new (fdisk) prompt. Type **o** to create a new partition table, then **w** to save it and exit fdisk. 

Now see if you can repartition it with gparted.

---

### Post by snakeman21 on 2009-07-03
Open a Terminal and type:

```
sudo chown yourusername /media/disk
```

replace "yourusername" with your actual username, and "/media/disk" with the actual mointpoint of the  device.

Good luck!

---

### Post by Toriam on 2009-07-04
zeirha,
I tried you advice on my 16 gig thumb drive and it worked perfectly, I'm having trouble with the 2 gig one though, and the sd card in my reader. The  2 gig says it doesn't want to mount, but it shows as being mounted, and gparted won't see my sd card?  Huh? Oh and I also tried the chown methold suggested, but that created several errors on both devices.
beth

---

### Post by geirha on 2009-07-04
Could insert both the SD card and the 2 gig drive, wait some seconds for them to settle, then run these two commands in a terminal:
```

sudo fdisk -l
mount

```

And post the output of those commands here? 

(Post terminal output in code-tags please, as it's easier to read then. If you use the quick-reply button to reply, click the Go Advanced button. In the advanced editing box, there's a #-icon in the toolbar, which adds the code tags.)

---

### Post by Toriam on 2009-07-06
For the SD card:
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaead4529

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 8017 MB, 8017412096 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000563f4

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         927     7446096   83  Linux
/dev/mmcblk0p2             928         974      377527+   5  Extended
/dev/mmcblk0p5             928         974      377496   82  Linux swap / Solaris
 
And the usb drive:
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaead4529

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fe37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   83  Linux

And I get an error message that says the drive won't mount, well here that is too: mount wrong fs type, bad option, bad superblock on /dev/sbd1/, missing codepage or helper program, or other error, in some cases some useful info is found in syslog, try   dmesg/tail or so

Whew! That wouldn't let me cut and paste. And then I attempt to mount the drive it's greyed out (and the places section on the top panel is too BTW), but the light on the drive still blinks a little.  
The sd card I mistakenly installed Xubuntu on when I was trying to install on the hard drive. Oh, and any way to get my second card reader on my computer working too? All this is happening on my acer aspire one.
:)) Beth

---

### Post by geirha on 2009-07-06
Could you also provide the output of ```
mount
``` when both the sd card and usb drive is connected? It will list all currently mounted filesystems. Also, the content of /etc/fstab would help. I suspect there's an entry for your 2 gig USB drive.

Anyway, with the 2 gig drive, try:
```
sudo umount /dev/sdb1
``` to ensure it is unmounted, then see if you can get gparted to partition it.

As for the other card reader, this page mentions that it only works if there's a card in it when you boot [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by Toriam on 2009-07-12
toriam@Acer:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

toriam@Acer:~$ sudo umount /dev/sda1
[sudo] password for toriam: 
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


The card stays in my computer as a storage expansion, I think I've taken it out twice since I've had this computer.

---

### Post by geirha on 2009-07-12
According to that output, it's not mounted, so gparted should allow you to repartition it ...

---

### Post by Toriam on 2009-07-12
That's what I thought. Thanks once again! You've been a real help! Maybe I did something wrong in the past, practice makes perfect.

---

### Post by Toriam on 2009-07-15
I managed to get the 2 gig usb stick partitioned. No luck on the SD card still. But both things give me the same error message at times:
when i push my sd card back in , this msg pops up: 
failed to mount SD/MMC
the enclosing drive for the volume is locked

so is the problem not with the card but the slot it's in? I'm so confused.

and the newly-partitioned stick says the same thing when i try to mount it.

---

### Post by Toriam on 2009-07-15
Never mind, I have the stick fixed.

---

### Post by Toriam on 2009-07-15
All fixed, clean card,thanks for your help!

---

