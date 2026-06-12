---
title: "Problems accessing CD/DVD Data"
date: 2011-12-17
forum: General Help
---

### Post by apollothethird on 2011-12-17
I had backed up data from an old hard drive onto a couple of dvd disk.  I'm sure I used Brasero as always.  However in this case, I can't mount the disks.  I get an error that says:

```

mount: you must specify the filesystem type

```The dmesg log shows:
```

[232116.279339] EXT3-fs (sr0): error: can't find ext3 filesystem on dev sr0. 
[232116.435562] EXT2-fs (sr0): error: can't find an ext2 filesystem on dev sr0. 
[232116.565838] EXT4-fs (sr0): VFS: Can't find ext4 filesystem 
[232116.780029] ISOFS: Unable to identify CD-ROM format. 
[232116.904805] FAT-fs (sr0): bogus number of reserved sectors 
[232116.904813] FAT-fs (sr0): Can't find a valid FAT filesystem 

```I also tried:

```

sudo mount -t iso9660 /dev/cdrom /mnt2/temp

```The data is on the disks.  I can see it with the cli: “strings /dev/cdrom | less”.

Anyone have any idea what I can do to recover the backed up data?  I tried using th DVD recovery program, ddrescue. 

```

ddrescue -n -b 2048 /dev/dvdrw mydisk.iso out.log

```It created an ISO of the disk of which the loop back mount give the same errors.

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by hugolia on 2011-12-18
I am having the same problem.
I created some DVD data disk to backup files, but cannot access its contents.
When I insert the disk in the drive nothing happens. In the Nautilus Computer folder the CD/DVD drive dissapears when the new DVD is inserted in the drive.
I've tried reading other older data disks and have no problem reading them.
Problem seems to be when mounting the recently created data disks.
I even tried creating an iso with brasero, and when I tried to mount the iso image, it mounts to an empty folder. But if I access the iso file with Archive Manager can read and access the data inside the iso.
So it seems that problem is with Brasero, and the data image it creates.

Hugo

---

### Post by Synoc on 2011-12-18
wish I could help. everytime I try to mount a CD/DVD the terminal goes unresponsive, sometimes to the extent that even CRTL+C won't bring it back up right away. I am presently searching the MAN pages for reason.

---

