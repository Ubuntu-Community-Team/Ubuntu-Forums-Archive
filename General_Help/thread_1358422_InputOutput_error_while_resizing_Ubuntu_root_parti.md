---
title: "Input/Output error while resizing Ubuntu root partition"
date: 2009-12-18
forum: General Help
---

### Post by cj.surrusco on 2009-12-18
I have an extra 6GB of unallocated space on my Hdd. So I booted to my ubuntu live CD and attempted to resized the Ubuntu root partition(ext4) to fill that space. About 90% of the way through reading the partition, it stops and under libparted messages it says that there was an input output errror. Why might this be happening?
Thanks,
CJ

---

### Post by internalkernel on 2009-12-18
Well... unfortunately, and as you probably already suspect. I/O errors probably have to do with the drive, it could mean a lot of things... not necessarily that the drive is bad or anything - mostly likely bad sectors in that drive. 

Try running fsck on the drive that you are resizing. Make sure it's clean... If that comes back clean, create an empty partition on that 6GB space and fsck that as well... if no errors for either, give it another try. 

```
fsck -a /dev/sdXX
```

where /dev/sdXX is the location of the partition you are working with...

I assume the I/O error message only happens during Gparted resize, and not during any other operations - just want to make sure the CD is not kicking off those errors.

---

### Post by cj.surrusco on 2009-12-18
I did the command for the root partition, and it showed up clean. Also for a new partition in the space, it came up clean.

---

### Post by internalkernel on 2009-12-18
What directory are you trying to expand the / or /home?

---

### Post by cj.surrusco on 2009-12-18
My home folder is in my root partition. So it would be the / partition, right?

---

### Post by internalkernel on 2009-12-18
yes unfortunately... I was hoping it was just the /home drive, so you could back it up and wipe it. Not sure what is going on exactly, but if it does have to do with bad sectors on the drive that's a problem that will only get worse. One of the only ways to fix it is a low level format - for bad sectors. I'm not entirely convinced this is the issue, since the fsck came back clean though. 

Who knows it maybe the LiveCD you are using... perhaps it's corrupted in just the right spot... Did you try to check the CD in the first boot menu?

---

### Post by cj.surrusco on 2009-12-18
Yes, I have. I've tried both the Gparted Live CD and the Ubuntu Live CD. Both give me the same problem.

---

### Post by dcstar on 2009-12-19
> **cj.surrusco said:**
> Yes, I have. I've tried both the Gparted Live CD and the Ubuntu Live CD. Both give me the same problem.

Then you have bad blocks on your hard disk. You may want to use SMART software to initiate a test of the disk.

---

### Post by dcstar on 2009-12-19
> **internalkernel said:**
> yes unfortunately... I was hoping it was just the /home drive, so you could back it up and wipe it. Not sure what is going on exactly, but if it does have to do with bad sectors on the drive that's a problem that will only get worse. One of the only ways to fix it is a low level format - for bad sectors. I'm not entirely convinced this is the issue, since the fsck came back clean though. 


fsck only checks the directory structure, it does not do any tests on the data area.

---

### Post by cj.surrusco on 2009-12-19
> **dcstar said:**
> Then you have bad blocks on your hard disk. You may want to use SMART software to initiate a test of the disk.
 
Will this be able to solve the problem?

---

### Post by cj.surrusco on 2010-01-02
I was never able to solve this problem, I just reinstalled ubuntu on an ext3 file system and I was able to resize and move that partition.

---

