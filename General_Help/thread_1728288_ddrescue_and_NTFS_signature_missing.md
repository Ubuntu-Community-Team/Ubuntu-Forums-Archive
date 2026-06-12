---
title: "ddrescue and NTFS signature missing"
date: 2011-04-13
forum: General Help
---

### Post by Eric.B on 2011-04-13
I've recently created an image of a windows NTFS drive using ddrescue.  There were very few errors and I tested the image using testdisk it tests ok.  

The problem I'm having is related to mounting it and accessing the data.  Apparently there is no partition table and I've tried a number of things...here's one example:

sudo mount -t ntfs -o loop,force hdimage.dmg /mnt/recover
NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I'm stuck...it's not a vfat format either.

Thanks....

---

