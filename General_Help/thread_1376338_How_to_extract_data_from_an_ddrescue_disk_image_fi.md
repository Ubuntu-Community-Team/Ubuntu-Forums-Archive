---
title: "How to extract data from an ddrescue disk image file"
date: 2010-01-09
forum: General Help
---

### Post by Spaarkplug on 2010-01-09
Hi,

I did a dd of a hard drive which was about to crash and saved the image file into a new external hard drive. The image file is single file of file size 160 GB.

My question.

1.) I do not know how to mount the image file. I know I have to do fdisk -u -l and then the location of the image file. However, then it gets complicated for me, I have no idea how many cylinders I have on the new media. and besides, most importantly, I do not want to recover the entire 160 GB, I only need to recover one single file from a certain folder of the huge 160GB disk image file. I know exactly where my file is, but I dont know how to mount the disk image and then get to my file.
2.) I also do not have 160GB of free space in my new laptop's hard drive. Is there a way to extract one file from my HUGE single image file?

How do I do this???
Do I need to first mount the image file, and then search for the file I need and then copy it? Do I need 160GB of freespace to do this?
How can I get my file? How do I extract. Help.

Thank you.

---

### Post by OldGrantonian on 2010-01-09
I found some google references to "foremost". This is in my synaptic (Karmic), and mentions dd files.

I've never used this. If you do, maybe you could give some feedback :)
.

---

### Post by mk1w86 on 2010-01-09
This might help::-k

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

---

### Post by iponeverything on 2010-01-09
It is pretty strait forward. If your image contains multiple partions see them like:

```
foo@mac:/media/disk$ fdisk -u -l imagefile.img 
You must set cylinders.
You can do this from the extra functions menu.

Disk imagefile.img: 0 MB, 0 bytes
32 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07443446

        Device Boot      Start         End      Blocks   Id  System
imagefile.img1   *          63      499967      249952+  83  Linux
imagefile.img2          499968      997919      248976   83  Linux

```

Say we want to mount the second partition inside the image above:

Multiply the start sector of 499968 by 512 which is the sector size reported by fdisk and this gives us: 255983616 
This will be our offset. Mount partition via loopback like so:

```
sudo mount -o loop,offset=255983616 imagefile.img /mnt

```

---

### Post by zackboll on 2012-07-30
Thanks, I was able to mount one of the partitions from my ddrescue whole disk image that way.  The problem is, my filesystem is somewhat corrupt for that partition.  Is there anyway to run fsck on the ddrescue image, then mount the parition.  

For me, my partition starts on sector 2048.  Each sector is 512 bytes. The filesystem is ext4.

Thanks,
Zack

---

