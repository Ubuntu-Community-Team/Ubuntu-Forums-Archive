---
title: "drives not ready or not present on loading Ubuntu"
date: 2010-07-19
forum: General Help
---

### Post by Bandworthy on 2010-07-19
I have an annoying issue when loading Ubuntu it gives a message
sdc1 and sdb1 being not ready. I have to press S to skip the two messages and continue loading.

The problem is that sdc1 is my DVD drive and sdb1 is my USB drive,
so naturally they are not always present.. Its really annoying, is there anyway I fix this so it stops doing this every time I reboot.

Also I think its connected but if I do boot without these present, when i do plug for instance my usb drive in once loaded, it will not mount, I have to reboot with it plugged in.

---

### Post by Bandworthy on 2010-07-20
Ok noone?,  right heres what i think is happening.

Somehow in my complete linux incompetence i've set EVERY known removable or not drive to mount on boot while getting my windows ntfs drive to do this, this is why its trying to mount an empty dvd drive, my usb drive and even my hidden laptop dell partition on boot. 

I'd rather go back to the default only mounting it when i use it 
then have this issue.  So how would i go about removing mounting of NON linux drives/partitions on boot so its like it was on clean install again?.

---

### Post by J V on 2010-07-20
sdb and sdc are internal SATA drives, not your or usb drive...

Could you post the output of:
```
cat /etc/fstab
```

We can get it to ignore them on boot from there...

---

### Post by John Bean on 2010-07-20
> **J V said:**
> sdb and sdc are internal SATA drives, not your or usb drive..

How can you know that? I often have a valid /dev/sdb and sometimes a /dev/sdc, and they're both USB devices.

---

### Post by J V on 2010-07-20
phail, meant to say dvd drives xD

usb drives can be sd.. but dvd drives and the like are referred to as dvd, dvdrw, etc... and their contents as sr** mount command can give you more info...

Anyway yeah, we just need to "Prune" your fstab file so send us the cat and we'll send you the pruned version...

---

### Post by Bandworthy on 2010-07-20
Ok I know for sure sdc1 is my usb portable drive, I do use usb sticks also, so that could be sdb1. I just assumed dvd but i know sdc1 is the port drive for sure since it stops if its plugged in.

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=18ed87e1-9d2f-40f6-941d-da21ddc90d45	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=07D7-0707	/fat_files	vfat	defaults	0	0
#Entry for /dev/sda2 :
UUID=4414431614430A7E	/media/sda2	ntfs-3g	defaults,locale=en_AU.UTF-8	00
#Entry for /dev/sda6 :
UUID=29fbb049-f9e0-4d5b-8560-aed8a83a3872	none	swap	sw	0	0
/dev/sdc1	/media/sdc1	vfat	iocharset=utf8,umask=000	0	0
/dev/sdb1	/media/sdb1	vfat	iocharset=utf8,umask=000	0	0


```

---

### Post by John Bean on 2010-07-20
Remove (or comment out) those last two lines. USB drives will auto-mount when you plug them in, no need for the entries in fstab that are causing your problem.

---

### Post by Bandworthy on 2010-07-20
aha yes worked perfectly, not asking on boot and I can plug and unplug usb drives. While the NTFS is mounted from the start yay!.

quick and painless.

Thank you!

---

### Post by Bandworthy on 2010-07-20
Actually I've noticed an issue still,  my usb drive is not mounting when plugging in. I have to boot with it plugged in if i want to use it.

---

### Post by John Bean on 2010-07-21
> **Bandworthy said:**
> Actually I've noticed an issue still,  my usb drive is not mounting when plugging in. I have to boot with it plugged in if i want to use it.

Does it appear in "Places" when you plug it in?

---

### Post by Bandworthy on 2010-07-21
No it doesn't appear, it works perfectly if i have it plugged in on boot. I can also click safe removal and it powers down fine as a usb should.  

But if i boot without it plugged in until loaded, I can see it has power but Ubuntu is not seeing it at all.

---

### Post by John Bean on 2010-07-21
See if it appears in the output of ```
sudo fdisk -l
``` (that's a lower case "L")

Type that into a terminal before connecting the disk, plug in the disk and wait a few seconds then type it again. Anything changed?

What to check next depends on the outcome :-)

---

### Post by Bandworthy on 2010-07-21
Something odd happened when i tried this, I typed the command plugged it in and it mounted just fine.. I went what the!, and rebooted many times it wasnt working like before. I booted without then plugged it in didnt mount, I typed that command again and then a few seconds after it suddenly auto mounted. 

I'd swear its mounting after typing sudo fdisk -l

Could it be connected to the sudo command?.

Ok no drive connected , booted without it 

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       12240    98241902    7  HPFS/NTFS
/dev/sda3           12240       14594    18906113    5  Extended
/dev/sda5           12240       14490    18071552   83  Linux
/dev/sda6           14490       14594      833536   82  Linux swap / Solaris

```

When its mounted it seems to mount after doing the command??

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       12240    98241902    7  HPFS/NTFS
/dev/sda3           12240       14594    18906113    5  Extended
/dev/sda5           12240       14490    18071552   83  Linux
/dev/sda6           14490       14594      833536   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bd62374

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

```

I'll test this alot over next few hours to see if its just random or something..

---

### Post by John Bean on 2010-07-21
Do you have another USB drive to try? It would be informative to discover whether the behaviour is related to that particular device or all USB disks.

---

### Post by Bandworthy on 2010-07-21
Interestingly enough it all seems to be working now normally.

I tried my 8gb usb stick and it mounted fine, I thought thats great tried the usb drive and it did also!, rebooted about 5 times with both usb drive and stick out and so far they have both mounted fine automatically now.  

All I can think of is that I have not plugged the usb stick in since before the lines were commented out to fix the previous problem.  

I'm hoping that something might have been corrupted and maybe its been reset by this.   

Fingers crossed problem gone, I'll give it some time and see if its intermittent or permanent.

---

### Post by John Bean on 2010-07-21
Hmm. I don't like things that suddenly "fix themselves" but at least it's working now.

---

### Post by Bandworthy on 2010-07-22
> **John Bean said:**
> Hmm. I don't like things that suddenly "fix themselves" but at least it's working now.

yeah chance of it unfixing itself again hehe... I'll give a day or two and if I it comes back will post, if not i'll flick this to solved.

---

