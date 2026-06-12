---
title: "Making a common storage partition"
date: 2009-10-02
forum: General Help
---

### Post by ablom on 2009-10-02
I currently have Win XP and Ubuntu Jaunty dual booted on my laptop (250gbs hdd). The partitions are:

Windows --formatted as NTFS-- 110gb
/ --formatted as ext3-- 10 gb
/home --formatted as ext3-- 110GB
swap --formatted as swap-- 2gb

I'd like to know if there's a way to utilize one partition as a common folder that both Ubuntu and XP can access where I can store my music, downloads, videos, etc. I don't want to have to format my hard drive again, but I know that I'd have to change the /home partition to NTFS. Is there a way to do this using Gparted and without loosing the info on my /home partition?

---

### Post by blur xc on 2009-10-02
There's a driver you can install in xp that will allow it to read and write to ext3 partitions...  

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Otherwise, you can just create a blank ntfs partition by resizing your XP partition.  From what I understand though, you don't necessarily want to use gparted to mess w/ ntfs partitions.  I guess it's better to use a windows utility.

Good luck...

BM

---

### Post by SuperSonic4 on 2009-10-02
Nah, gparted is fine if you know what you're doing and you have the appropriate backend.

You certainly can. I do it for storing my media on. You will need to create a partition for data either by reducing windows (best done in windows) or /home (should be fine but back up any irreplaceable/important data).

You will also have to edit fstab if you want them to mount on boot

---

### Post by ablom on 2009-10-02
Thanks for the quick replies. I just want to correct my first post, all my ubuntu partitions are EXT4 not EXT3.

---

### Post by SuperSonic4 on 2009-10-02
Then you'll be very lucky to see it in windows, I would go with a ntfs partition.

---

### Post by ablom on 2009-10-02
Supersonic, in reply to your first post, I'm very new to gparted and am not very familiar with it at all. Never actually used it. Could you just explain what you meant or point me to a 'how to.'

---

### Post by blur xc on 2009-10-02
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

not directly related- but gives a look at how to run gparted- 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Might I ask, if you are already dual booting w/a separate /home partition, how you did that w/o using gparted?

BM

---

### Post by sisco311 on 2009-10-02
If I understand you correctly, you want to move your home directory to the root partition and format your home partition as NTFS.

You can use the Live CD. 
Mount the root and home partitions and move your home directory in the root partitions /home directory.

Format the partition as NTFS with GParted. GParted is GUI application with a quiet intuitive interface. Just Right click on the partition you want to format and select Format to... NTFS.

Edit the /etc/fstab file(the one located on your root partition)
and replace
```

UUID=<some random hex digits> /home               ext4    relatime 0 2
```
with 
```
UUID=<uuid of the ntfs partitio> /media/share        ntfs   defaults,dmask=002,fmask=113,gid=46 0     2
```

to get the uuid of the partition:
```
sudo blkid -c dev/null
```

NOTE: don't forget to create the new mount point (/media/share).

If you need step by step instructions, post the output of:

```
sudo fdisk -l
```
```
df -h
```

---

### Post by ablom on 2009-10-03
Thanks for all the replies. I think I've basically figured it out from the info that was posted now just have to hope I don't mess anything up.

---

### Post by jward3010 on 2009-10-03
Like others I highly recommend the single NTFS partition - Windows understands it, Ubuntu understands it - both can read / write to it without any problems. 

The fuse driver was originally for ext2 partitions, by default forward-compatible with ext3 because there was no extra additions to ext3 other than journaling, but I don't know what kind of development it's still in (it's not open-source for some silly reason) and my luck with it in the past wasn't worth the work I would have had to put in.

---

