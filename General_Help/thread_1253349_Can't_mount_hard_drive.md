---
title: "Can't mount hard drive"
date: 2009-08-30
forum: General Help
---

### Post by olbaldy77 on 2009-08-30
Hello, I'm having big issues mounting a hard drive. I formatted in ext2 while running 8.04.3 and yesterday upgraded to Jaunty. I had no problems with the drive in Hardy and the drive mounted, with no problems, the first time I booted into 9.04, but now it won't mount.

First I got: [B]mount: wrong fs type, bad option, bad superblock

[/B]I searched for help on that issue and found [this]("http://ubuntuforums.org/showthread.php?t=638713&page=2"). And I followed the advice of this post:

> **Re: mount: wrong fs type, bad option, bad superblock**             
                                                                Okay, did some more thorough digging on this forum and found [this]("http://pysdm.sourceforge.net/")
and this [http://ubuntuforums.org/showthread.p...problem&page=6]("http://ubuntuforums.org/showthread.php?t=582045&highlight=gutsy+usb+mount+problem&page=6")

sudo aptitude install pysdm

then sudo pysdm

then double click on the left menu to open your device (it must be plugged in, then click refresh) You can set all the options you want with it and then it should work just fine. Good luck to anyone else with this problem.
Rebooted and turned the hard drive off. Powered back on, turned the hard drive on and now I get this message when I try to mount the drive: 

> **Cannot mount volume.**

Invalid mount option when attempting to mount the volume.Now I've been searching for help on this issue and all I can find that pertains to this error is when it's associated with an external CD/DVD drive. Nothing that I've found so far helps with hard drives. And if there's a fix in the stuff I've read, I don't know how to translate that to my problem.

**Specifics:** *Computer*: Dell Dimension 8200, *Hard drive*: Western Digital 1TB WD1001FALS *Settings for the drive from pysdm*: name: sdb1; mountpoint: /media/sdb1; type: ext2; options: errors=remount-ro,users; in the mounting options: Allow any user to mount the file system

The most frustrating about this is, as I've mentioned, that the drive worked and now doesn't.:confused:  I think this is implied, but I have a lot of data on this drive that I would like to keep.

Please help and thank you for any support you can offer.

---

### Post by scouser73 on 2009-08-30
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by olbaldy77 on 2009-08-30
While searching for help, I came across [this]("http://ubuntuforums.org/showthread.php?t=885129") thread.

Followed the advice given.

> type "sudo fdisk -l"> sudo mkdir /media/external> sudo mount /dev/sdb1 /media/externalAnd I get this: > mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by olbaldy77 on 2009-08-30
I also gave this a shot:
> 
I noticed that there are so many problems with those who are unable to mount their USB Disk on Ubuntu 8.04.2. The message that pop up was: *"Invalid mount option when attempting to mount the volume"*. 

Here is a solution that I came across while surfing the web for more than 3 hours.

Step 1: Remove your USB/Flash Disk from your PC/Notebook/Netbook.

Step 2: Go to Applications > Accessories > Terminal and run the following command: **[sudo gedit /etc/fstab]**

Step 3: In the file you opened, you probably find a line like this:
**[/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0]**

Step 4: Comment it by adding a "#" like this:
**#/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0**

Step 5: Plug in your USB/Flash Disk again.

I hope this is of some help for those who need it.

Cheers!

Modified it for my hard drive and it to did not work.

---

### Post by Bucky Ball on 2009-08-30
```
udf,iso9660 user,noauto,exec,utf8 0 0
```That bit definitely won't work for a hard drive and could be one of the reasons you are getting an error. (Compare with other EXT partitions). This might work, it is for EXT3 partition though:

```
# /dev/sdb1
**UUID=48AF-C7CD**                            /media/external   auto   defaults,user,users,dmask=0000,fmask=1111   0   0
```You need to get the correct UUID number for your partition. This can be obtained with:

```
sudo blkid
```As far as I know, Jaunty uses the UUID in the fstab, NOT '/dev/sdb1  /media/external' to mount drives at boot. :)

---

### Post by olbaldy77 on 2009-08-30
New I probably should have done this to begin with, but somehow forgot. This is my fstab.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0  
# / was on /dev/sda1 during installation
UUID=586a52a5-3f0e-4b87-a122-2e8ff2c57909  /               ext3         relatime,errors=remount-ro          0  1  
# swap was on /dev/sda5 during installation
UUID=e0ec8827-7d17-4a12-94a3-9c5dc7b44e1f  none            swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0  
/dev/sdb1                                  /media/external ext2         owner,errors=remount-ro,users,user  0  0  
```Found the UUID ```
/dev/sda1: UUID="586a52a5-3f0e-4b87-a122-2e8ff2c57909" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e0ec8827-7d17-4a12-94a3-9c5dc7b44e1f" 
/dev/sdb1: UUID="ba7a3d7b-a5b4-4fb4-bd74-c4074f51d4f4" TYPE="ext2"
```I tried editing it like this. ```
# /dev/sdb1
UUID=ba7a3d7b-a5b4-4fb4-bd74-c4074f51d4f4                            /media/external   auto   defaults,user,users,dmask=0000,fmask=1111   0   0
```The result was this. > Invalid mount option when attempting to mount the volume.                      Since I have no clue exactly what I'm doing (I know, that really inspires confidence in me too:rolleyes:) I also tried this.
```
# /dev/sdb1
UUID=ba7a3d7b-a5b4-4fb4-bd74-c4074f51d4f4                            /media/external   etx2   defaults,user,users,dmask=0000,fmask=1111   0   0
```Which got me this.
> The volume uses the  file system which is not supported by your system.

Arrgh! But thank you very much for the try Bucky.

---

### Post by Bucky Ball on 2009-08-30
*** Don't know if you noticed but you have 'etx2' instead of 'ext2'. That could be your problem and would almost certainly cause the error you report.

Okay, maybe Jaunty doesn't support EXT2, but that would be unusual (but possible). You might still have part after 'ext2' wrong for ext2. 
```

# /dev/sdb1
UUID=ba7a3d7b-a5b4-4fb4-bd74-c4074f51d4f4                            /media/external   **ext2**   **defaults,user,users,dmask=0000,fmask=1111   0   0**
```:)

---

### Post by olbaldy77 on 2009-08-30
Bucky, haven't you heard? etx2 is a super fast and super safe new formatting option. It's so great that it only exists in my mind when I'm trying to type ext2 and going so fast that I don't proofread :P

Sadly, typing correctly did not change the problem :(

---

### Post by Bucky Ball on 2009-08-30
```
# /dev/sdb1
UUID=ba7a3d7b-a5b4-4fb4-bd74-c4074f51d4f4                            /media/external   **ext2**   rw, user 0 0
```
Try that. From this page:

[http://en.kioskea.net/faq/sujet-1856-access-disk-partition-ext2-3](http://en.kioskea.net/faq/sujet-1856-access-disk-partition-ext2-3)

---

