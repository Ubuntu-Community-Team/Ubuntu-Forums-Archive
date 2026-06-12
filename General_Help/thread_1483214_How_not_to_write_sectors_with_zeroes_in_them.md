---
title: "How not to write sectors with zeroes in them"
date: 2010-05-14
forum: General Help
---

### Post by qiet72 on 2010-05-14
Hi, 

I would like to restore a dd image from a file to a disk or partition but I don't want to write the whole image but only the sectors that have data in them (sectors that don't have zeroes in them).  I know you can that when writing to  a file, eg: zcat ddimage.gz | cp --sparse=always /dev/stdin filename.img

but you cannot do that to a device.  Is there a tool that can do that.  There are two reasons for this:
- restoring an image goes faster as I am only restoring sectors that have data in them (especially on slow write media).
- limiting the number of writes on flash media: why waste write cycles on flash media when you are only writing sectors with zeroes in them?

I would have used google to search but I have no idea how to describe to google what I am searching for.

qiet72

Solution: Use ddrescue's "-S" parameter.

---

### Post by dcstar on 2010-05-14
> **qiet72 said:**
> Hi, 

I would like to restore a dd image from a file to a disk or partition but I don't want to write the whole image but only the sectors that have data in them (sectors that don't have zeroes in them).  I know you can that when writing to  a file, eg: zcat ddimage.gz | cp --sparse=always /dev/stdin filename.img

but you cannot do that to a device.  Is there a tool that can do that.  There are two reasons for this:
- restoring an image goes faster as I am only restoring sectors that have data in them (especially on slow write media).
- limiting the number of writes on flash media: why waste write cycles on flash media when you are only writing sectors with zeroes in them?

I would have used google to search but I have no idea how to describe to google what I am searching for.

qiet72

A program like dd cannot assume that the destination is already full of "zeroes" and not copy what it has for that area.

The only way these things can be sure of copying an image is to copy the whole image.

---

### Post by tgalati4 on 2010-05-14
If you are doing data recovery, then it pays to get an extra drive and USB enclosure, then you can simply use the dd command and it will be reasonably quick.  Large write sessions to flash can be problematic.

---

### Post by srs5694 on 2010-05-15
In the future, you could use a backup tool that omits unused sectors. Something like ntfsclone (for NTFS) or dump (for ext2/3/4) will do the job, as will tar or dar on a file-centric level. Some of these may require you to re-install boot loaders if any were present in the partition's boot sector.

---

### Post by qiet72 on 2010-05-16
ntfsclone is a very good example and I have used it alot - but it is only for the ntfs file system.  Anyways, I noticed that the latest version of  ddrescue has a feature called sparse files (-s).  I will try that out and see if it does the job. :)

qiet72

---

### Post by qiet72 on 2010-05-16
I found my solution: "ddrescue -S" works very well - it can write sparsely both to files and devices.  :-)

qiet72

---

