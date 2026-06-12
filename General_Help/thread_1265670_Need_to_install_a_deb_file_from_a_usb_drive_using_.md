---
title: "Need to install a deb file from a usb drive using terminal"
date: 2009-09-13
forum: General Help
---

### Post by otz070 on 2009-09-13
ok I'll save the long story, but heres what I got:

1. Network Manager deb file on a Kingston usb drive.
2. I have no file manager, so I have to use terminal...(basically I forgot to add it before I screwed the network)
3. Running a fresh Jaunty install...a very stripped down one...was in the process of optomizing.

pretty much what happened was I tried lxnm, which doesn't work so well...

see the problem is that I don't exactly know where on my system the drive is supposed to be. 
what I found is this:
```

cd /media
media$ find
.
./.hal-mtab
./cdrom
./cdrom1
./cdrom0

```

I would figure that the drive would be in media right? Tried each of those and its not.

Any help is appreciated:)
Thanks in advance

---

### Post by NoaHall on 2009-09-13
Have you mounted it? Post the output of "mount"

---

### Post by otz070 on 2009-09-13
ok I tried to mount it, but I don't know where it is. I don't have internet on that computer, so I'm using the one sitting beside it:). Anyway, on the computer I copied it from (intrepid ubuntu) it shows up as "Kingston" 
so I put this in and got:
```

mount Kingston
mount: can't find Kingston in /ect/fstab or /ect/mtab

```

I also tried other things aside from "Kingston" after mount, but no luck...

---

### Post by NoaHall on 2009-09-13
I meant just do "mount" and post the output.

Also do "cat /etc/mtab"

It'll be called something like sdb2 or something, not kingston before mounting.

---

### Post by sisco311 on 2009-09-13
First you have to determine what the partition is called:
```
sudo fdisk -l
```

i.e.
```
sudo fdisk -l
...
Disk /dev/sdb: 20.0 GB, 20020396544 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System
**/dev/sdb1 * 1 19457 16490691 7 HPFS/NTFS**
```
(If you are unsure which is the usb drive, just post the output of the command.) 

Then you have to create the mount point:
```
sudo mkdir /media/disk
```

And finally mount the partition:
```
sudo mount -t auto /dev/sdb1 /media/disk
```

```
cd /media/disk
```

---

### Post by otz070 on 2009-09-13
um thats alot because I have to type it all out...

thanks sisco311:D

found it on /dev/sdf1 (easy to spot cause its the only one in FAT format:))

---

### Post by sisco311 on 2009-09-13
never mind

---

