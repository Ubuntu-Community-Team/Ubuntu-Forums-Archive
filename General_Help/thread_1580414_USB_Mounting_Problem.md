---
title: "USB Mounting Problem"
date: 2010-09-23
forum: General Help
---

### Post by ZhuaSD on 2010-09-23
Hi All, I got a big problem and could use some help.

I have an external hard drive that sometimes is called sdb and sometimes sdf that I want to mount, but it wasn't mounting right.  It was making two entries, one which sort of worked and one which didn't. It was making entries as both USB0 and the volume label, but the access was not very good, and it just got worse. Even though it said it is mounted, the window just hangs and blackens out when I try to access it. 

So I tried to use the Storage Device Manager, at that point (after unmounting with gparted, the only thing that worked) it was showing up as sdf.  Well then I got the error on startup, disc not available do you want to wait or skip.  And the volume is showing up as sdb but its not accessible and the data info I see in Gparted is wrong (says only 150 mb is used).

I have tried to use Mount Manager, Storage Device Manager, and all I did was mess up my system.  At this point I have no access to the drive.

I checked my fstab, and even though I have lots of internal partitions for my data (which I think is a mistake in Ubuntu), the fstab had only one entry, now there is two after I put another one in there with storage device manager:
```
proc                                       /proc        proc nodev,noexec,nosuid  0  0  

/dev/sda2                                  /            ext4  errors=remount-ro    0  1  
UUID=5e34bc1c-25ee-46d5-843c-c9cf372e648d  none         swap  sw                   0  0  

/dev/sdf1                                  /media/sdf1  vfat  defaults             0  0  
 
```

but its still there as sdb anyway.

:popcorn:

Any help on this?  I need to get rid of the wrong entries and make the right ones.  

And I could use some support through this, I have searched around and figured some things out, but not really how to remove the wrong points.  

I am also really surprised, why is my fstab so empty?  Should all of those partitions on sda be outside of fstab?

Here is fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2439    19591236   83  Linux
/dev/sda2            2440        5113    21478905   83  Linux
/dev/sda3            5114        5242     1036192+  82  Linux swap / Solaris
/dev/sda4            5243       30401   202089637    f  W95 Ext'd (LBA)
/dev/sda5            5243       13605    67175766    b  W95 FAT32
/dev/sda6           13606       30401   134913838+   b  W95 FAT32

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf48786e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

```


Here is dmesg | tail -n 25:
```

[   78.384583] CPU0 attaching sched-domain:
[   78.384587]  domain 0: span 0-1 level MC
[   78.384590]   groups: 0 1
[   78.384597] CPU1 attaching sched-domain:
[   78.384599]  domain 0: span 0-1 level MC
[   78.384601]   groups: 1 0
[   86.320523] eth0: no IPv6 routers present
[  133.916030] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  166.928031] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  198.916038] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  231.920053] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  264.916036] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  605.100031] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  638.100097] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  670.100132] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  703.100052] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  736.100113] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  769.100054] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  801.100055] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  833.104135] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  866.100051] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  899.100165] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  932.100044] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  965.100038] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  998.100039] usb 1-4: reset high speed USB device using ehci_hcd and address 3

```

---

### Post by mikewhatever on 2010-09-23
By default, fstab only contains the Ubuntu system partitions. You can add more entries, but they are not required. As for the external hdd, can you post its model. I've heard that some hdds may have virtual partitions/virtual disks.

---

### Post by ZhuaSD on 2010-09-23
Hey Mike, thanks for the comment.

Its a Western Digital.  

I should make clear that this drive used to mount fine, but then later the mounting got messed up.  The disc checks out fine.

I am trying to remove old mount points so that I can re-mount this drive properly.  Maybe that is clearer.

---

### Post by ZhuaSD on 2010-09-24
I want to try to be clearer to get to some resolution.  If not, I will just re-install I guess, yet again. That's easiest for me to do.  Because if its mounted right it will work fine, but right now I have no access to the drive.

When I used the Storage Device Manager, it made an entry into my fstab.  But this has led to the evil Drive not ready or not available on startup.

I guess basically my problem is I have multiple mounting info for this drive. I want to remove them, how can I?

I have found lots of info on mounting drives, what I really want now is how to remove all these extra ones and get a fresh shot.  Editing fstab is not a huge issue, but if I remove the fstab entry it just ends up getting mounted as usb0 and that's still not helpful.

How to remove these things and get a fresh start?  Anyone pls??

:guitar:

---

### Post by mikewhatever on 2010-09-24
Many a time, partitions wouldn't mount or would mount as read only because of file system errors. When is the last time you checked it? Different mount points don't matter, but what are, and where are the old mount points you keep mentioning?

---

### Post by ZhuaSD on 2010-09-24
Thanks again Mike. I just check the drive, no problem.  I didn't expect a problem because I have had trouble mounting this drive through several installs of Ubuntu, so I knew it was a mounting issue.  But I checked it a day or so ago, because I was using gparted anyway to unmount.

I think I might have found some solutions, the mounts are under /mount, and these two pages seem to help:

```
https://help.ubuntu.com/community/RenameUSBDrive
```

and 

```
https://help.ubuntu.com/community/MoveMountpointHowto
```

The problems are a little scary.  The drive mounts even when I don't want it to, even when I select skip mounting, but still no access.  And all of this temporarily screws up my places file, so that two internal drives are listed twice, another external drive I have attached shows up ok, but in gparted it warns me that its not mounted right...I am afraid of messing up my system more.  

Editing fstab is not a problem but it seems like I have to edit a bunch of places just to get back to square one.

It just seems strange, why can't I use one application to handle this, rather than having to remove files from /mount, maybe from /mnt (if I can find that directory) and fstab.

Anyway, I will check into it.  For now, I think I will mark this thread as solved, and if I still need help I will start a new thread.

Thanks again, my friend.  :)

---

### Post by ZhuaSD on 2010-09-24
Ooh, here is a bug that seems to be exactly the original problem I had with this drive, before I fuXXored my system.  I didn't know it was unmounting but the behavior (temporary stopping of media files from the drive) is exactly what the problem is:

```
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349767
```

---

