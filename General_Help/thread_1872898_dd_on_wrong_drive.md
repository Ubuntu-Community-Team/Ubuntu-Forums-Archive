---
title: "dd on wrong drive"
date: 2011-10-31
forum: General Help
---

### Post by ELMIT on 2011-10-31
Something gone wrong!!!

I have a 2 GB flashdrive and a 1.5TB USB hard disk

I mounted /dev/sdc1 as /media/disk   (1.5 TB)
I plugged in the 2GB flashdrive and according to the history I did:

sudo dd if=binary.img of=/dev/sdd

It gave me an error at the end.

I noticed that my drive /media/disk appeared twice in Nautilus !!!
I could not re-mount it, so I restarted the computer and it seems that I have overwritten with 512MB onto the 1.5TB disk.

fstab:
# Entry for /dev/hde1 (1.5 TB USB hard disk)
UUID=08C48463C484553A /media/disk ntfs-3g defaults,locale=en_US.UTF-8 0 1


How can I save the most of the hard disk?

bye

Ronald

---

### Post by ELMIT on 2011-10-31
blkid shows:
/dev/sdc1: SEC_TYPE="msdos" LABEL="UbuntuCloud" UUID="A7AB-2B6B" TYPE="vfat"

but should be:
UUID=08C48463C484553A /media/disk ntfs-3g defaults,locale=en_US.UTF-8 0 1

---

### Post by WasMeHere on 2011-10-31
Hi ELMIT,

If you have really overwritten part of your disk, that part can not be recovered by regular people (maybe by the intelligence service of a superpower state). But the rest of the data are still there, as long as you avoid writing operations.

The situation is better if there are several partitions, because the partitions starting outside the overwritten part are good, and it may be possible with some tool (e.g. ***gpart***) to 'guess' a partition table that works for it. In the partition that was damaged, file data outside the damage can be recovered by some other tool (e.g. ***PhotoRec***). However, the directory structure will be lost, and probably also file names unless they were stored inside the files.

With help from some of us at the Ubuntu Forums you will get back most of your data, but you'll have to work for it.

Good luck
Olle

---

### Post by WorMzy on 2011-10-31
Oh dear. I'm sorry to say that, if what you say is correct, then you've probably destroyed a significant portion of your data. If you have backups, now is the time to restore them. Otherwise, you'll have to try and use data recovery software to salvage what you can.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

In future, make sure you're absolutely positive that you've got it right before executing a dd command. It isn't nicknamed the "data destroyer" for nothing.


Also,
> UUID=08C48463C484553A /media/disk ntfs-3g defaults,locale=en_US.UTF-8 0 1 

This is an fstab line, not blkid output. It is also wrong. The only partition that should have a "1" at the end is the one that gets mounted as /; everything else should have a "0" or a "2".

---

### Post by ELMIT on 2011-10-31
Thanks, ... 

I have installed gpart. I have only one partition on that drive!


$ sudo gpart /dev/sdc1

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


What am I doing next?

---

### Post by ELMIT on 2011-10-31
gparted shows now:

Partition FileSystem MountPoint            Size      Used Unused Flags
/dev/sdc1  fat16     /media/UbuntuCloud    530 MiB   513.25 16.75 goot
unallocated                                1.36TiB

---

### Post by WasMeHere on 2011-10-31
If you have only one partition, the information about it seems to be wiped and ***gpart*** cannot output anything but zeros. Do you have any backup files or any files with information about the partitions?

Try also ***TestDisk***! There is still ***PhotoRec***, but it is definitely not as convenient.

---

### Post by ELMIT on 2011-10-31
Got following output, what am I doing next?


TestDisk 6.13-WIP, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 22892791 4 32

The harddisk (1500 GB / 1397 GiB) seems too small! (< 3597 GB / 3350 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  FAT16 LBA            21345837   2 22 54900235   0 26 4294962885
   FAT12                23535314   3 12 26117206   0 12  330482081
   FAT32                25689940   2 17 48912917   1  7 2972541015








[ Continue ]
2199 GB / 2047 GiB

---

### Post by WasMeHere on 2011-11-01
I'm sorry ELMIT,

TestDisk cannot identify your old ntfs partition. Now you have tried two possible fast ways to recover files. I think it is time to start with ***PhotoRec***.

It was originally made to recover photo files from flash cards, where the file system had been destroyed. This happened often in the early days, when people did not know the risks when pulling out the card before it was unmounted, but also because some computers could not handle some cards, for example 'too' new or big cards. It happened to me once.

Today PhotoRec is a versatile utility, that can recover data from many different file types looking at the header data. This means that it works even without proper information about the partition, as long as the file data is not overwritten. So all your files 'behind' the overwritten (512MB?) part can be recovered with PhotoRec. However, the directory structure will be lost, and probably also file names unless they were stored inside the files.

Good luck
Olle

---

### Post by ELMIT on 2011-11-01
Ok, ... 

Somewhere on the way I need to get the drive to an NTFS file system again. When and how do I do that? THEN (???) I can try PhotoRec, right?

---

### Post by WasMeHere on 2011-11-01
No, PhotoRec works on the disk as it is. If you make it an NTFS disk, you probably destroy your data.

1. Recover your data
2. Make partition(s) on the disk again

Read the instructions about PhotoRec and download it from the internet!

*Edit: You need a drive where to write the files, that will be recovered. If you don't have one, borrow or buy one!*

---

### Post by infinitybot on 2011-11-01
Maybe you could try ddrescue?
```
sudo apt-get install gddrescue

```

---

### Post by WasMeHere on 2011-11-01
> **infinitybot said:**
> Maybe you could try ddrescue?
```
sudo apt-get install gddrescue

```

I think ddrescue's main purpose is to save what can be saved from a disk with read errors (damaged hardware). In this case, I think that the disk hardware is good. It is 'only' the software that is damaged: the beginning of the partition and its file system is overwritten by a copy of another file system.

---

