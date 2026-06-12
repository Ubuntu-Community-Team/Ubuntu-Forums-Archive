---
title: "Can't mount NTFS ddrescue image of partition."
date: 2010-06-14
forum: General Help
---

### Post by buildupnow on 2010-06-14
Hello,
First off I am a major newbie at all of this (linux, ubuntu, code, etc) I have spent the last week trying to figure it out and I am finally stuck!!

I am trying to recover some important data from a 273 gig NTFS partition that was used in windows 7. The laptop was dropped and would not boot the next day. As an external drive I could see 2 smaller partitions (30 gig and 500 meg), but the main partition was RAW and requesting to be formatted... so I came to learn about Knoppix 6.2.1 as my live boot cd and ran ddrescue to recover an almost complete image of the bad partition

**ddrescue -n /dev/sdc1 /media/sda1/image.img /media/sda1/logfile.log**
I then ran it one more time:
**ddrescue -r 1 /dev/sdc1 /media/sda1/image.img /media/sda1/logfile.log**

the image was made with 741 errors (amounting to 160 megabytes)
----
So Now I have my partition as image.img which I want to mount.

First I tried
[B]sudo mount -t ntfs -o loop /media/sda1/image.img /mnt/recovered
sudo mount -t ntfs -o loop,force /media/sda1/image.img /mnt/recovered[/B]
(and some variations)
I get the following error:
NTFS signature is missing. 
Failed to mount '/dev/loop/0': Invalid argument
The device '/dev/loop/0' doesn't seem to have a valid NTFS.

I read elsewhere since it is an image I do not need the **-t ntfs** tag (but then I get the following error)
:you must specify the filesystem type


So then I tried:
**testdisk /media/sda1/image.img**
and ran a deep scan
results: -272GB/254Gib - CHS 33177 255 63
analyse cylinder 33176/33176: 100%
it came back with no information on a partition (no start/end)
I am not sure if I used testdisk correctly as it seems that all it was trying to do was determing the start/end of a partition... but the image is only of 1 partition so the start and end would just be the beginning and end of the image?


**fdisk -l **
I get back information from the original bad disk as such:

/dev/sdc1:     Start: 1   End: 33177       Blocks: 266494221    ID: 7   System: HPFS/NTFS   (This is for the main partition that I Imaged)

which seems to indicate that the filesystem is still recognized (somewhat) and knows that it is NTFS (7)....

Not sure how to proceed.... hoping to be able to mount instead of trying out the photorec process

---

### Post by cbrunhaver on 2010-06-14
The easiest way to find and mount an ntfs partition would be "ntfs-config" which is a gui utility for ntfs-3g preinstalled under "system tools".

[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

