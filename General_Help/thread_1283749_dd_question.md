---
title: "dd question"
date: 2009-10-05
forum: General Help
---

### Post by ttallos on 2009-10-05
I have made several dd images of a 3.2 Gig HDD. What is the command to mount the image using a loopback device? I want to try to recover some data. Thanks.

---

### Post by niteshifter on 2009-10-05
Hi,

Assume somefile.img is your 3.2GB image made with dd. Also assume /media/image as the mount point:

```
sudo mount -o loop /path/to/somefile.img /media/image
```
Will mount somefile.img at /media/image and mount will attempt to guess what file system is present (works well usually).

Same as above but read-only:
```
sudo mount -r -o loop /path/to/somefile.img /media/image
```



```
sudo mount -t ext3 -o loop /path/to/somefile.img /media/image
```
Will force mount to treat the image file as having an ext3 file system.

```
sudo mount -t vfat -o loop /path/to/somefile.img /media/image
```
Will force mount to treat the image as having a FAT file file system.

Same as above, read-only:
```
sudo mount -r -t vfat -o loop /path/to/somefile.img /media/image
```

---

### Post by ttallos on 2009-10-06
Thank you for your help I really searched all over the web for the right answer first. Since this is such a small drive I have Image.001 and Image.002 I just wrote the command for Image.001 in the example below with the error message listed. This is just a data recovery experiment I am doing trying to learn how to use the tools dd, air, dd_recover etc etc. do I need to somehow get the second file (Image.002) in the command each image file is 2G? I can reimage the drive if I need to....

mount -o loop /home/default/4_Files_Delete/Image.001 /media/image  
Failed to read last sector (6346304): Invalid argument 
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, 
   or it was not setup correctly (e.g. by not using mdadm --build ...), 
   or a wrong device is tried to be mounted, 
   or the partition table is corrupt (partition is smaller than NTFS), 
   or the NTFS boot sector is corrupt (NTFS size is not valid). 
Failed to mount '/dev/loop0': Invalid argument 
The device '/dev/loop0' doesn't seem to have a valid NTFS. 
Maybe the wrong device is used? Or the whole disk instead of a 
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by bigboy_pdb on 2009-10-06
You might also want to look into [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec"). Also, in a worst case scenario, you can use a file dump utility such as octal dump (od) to view the contents of the image if need be.

With respect to your question, I think the images need to be one image if you're going to try and mount them.

---

