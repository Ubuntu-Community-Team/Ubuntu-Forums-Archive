---
title: "I formatted usb disk to ext3,it has only 90% available space it should've. How come?"
date: 2006-05-05
forum: General Help
---

### Post by sup on 2006-05-05
I bought a 250GB usb external hard drive. It has actually only 231GB, but it was expected, as 250GB means 250*1000*1000*1000KB and here not 250*1024*1024*1024KB as usual. However, when I formatted the disk into ext3, it seems there is only 219GB free space out of 231GB available, although I have not written any files on the drive. How is that possible?

I know that when I installed Ubuntu, it took some space (5 or 10%) of my internal drive for root's purposes (or something like it, I do not remember it very clearly) - does it have something with common with issue above? It is not really necessary for USB drive, is it?

---

### Post by Choad on 2006-05-05
im not 100% sure, but i think ext3 is a rather posh system that uses up a bit of the disk space to make access faster or something. its possible that space was taken up by the actual file system it's self.

---

### Post by JoeMetal on 2006-05-05
I formatted a .5TB external drive and it went down to 476.5GB.  It has to do with setting up the filesystem.  That was fine for me because ~475GB is still a hell of a lot of space.  Maybe try other filesystems? ext2? reiserfs?

---

### Post by lha on 2006-05-05
When a drive is formatted as ext3, 5% of space is reserved for super user. You can select another percentage if you want. See 'man mkfs.ext3', look for -m.

sup: 231/219=0.94805
JoeMetal: 476.5/500=0.95300
As you see, 5% is reserved.

---

### Post by bionnaki on 2006-05-05
...yes, or just format with reiserfs.

---

### Post by yabbadabbadont on 2006-05-05
Also, a significant portion of the space is taken up by the journal that is created when formatting with ext3.  If you don't want journaling and want max space available, try ext2 instead.

Something like:

mke2fs -m 0 /dev/???

(-m 0 tells mke2fs not to reserve any space for the superuser)

---

### Post by sup on 2006-05-08
double posted, sorry

---

### Post by sup on 2006-05-08
Than&#7729; you all, the -m 0 option made 146.5 GB out of 146.7GB available - journal is not obviously very big. Although I am not sure if its benefits are of any importance to me in this case, I think 200 megabytes is not worthy using something as ancient as ext2 is said to be.

BTW:reiserfs and like are not suitable for me since an external hard drive is also means of exchange of data with other people who often run windows and as far as I (and wikipedia) know, onlu ext2/3 have reaw/write support under windows using ifs drives.

BTW2:gparted, partition magic and any gui program that has anything to do with partitioning suck, at least for me, fdisk mkdosfs and mke2fs works faster, better and offer more options - and they seem no to be doing some silly things that make disks not even been seen by the computer and so on.

BTW3:does anyone knows what volume label is for?

---

### Post by sup on 2006-05-08
just found out that volume label when set up determines the name of directory in media where the wolume will be mounted - which is nice, although I do not know how to set it without reformating the disc - luckily it is empty right now

---

