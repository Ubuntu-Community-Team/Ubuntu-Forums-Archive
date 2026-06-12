---
title: "How to format 2GB USB Flash Drive"
date: 2009-10-29
forum: General Help
---

### Post by Jason Cook on 2009-10-29
I have a 2GB USB flash drive and I am wondering which format I should use. I would like to be able to use it in Windows. Please include that program to format it with.

---

### Post by bodhi.zazen on 2009-11-05
Moved to general help (the tutorials section is not for support questions).

You can use FAT (vfat), ntfs, ext2, or ext3. both FAT and ntfs will work out of the box.

To use ext2/3 you will need to install the windows drivers :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

To format your drive you can use garted or the command line.

To use gparted, install it =)

To use the command line use mkfs.vfat or mkfs.ext2

ex

```
mkkfs.vfat /dev/sdb1
```

Just be sure to understand partitions first.

---

### Post by ivanvajar on 2009-11-05
You can use any partition editor to format USB drive. Gparted can do the job just fine. If you want USB flash drive to be visible on any Win machine, use FAT or NTFS filesystem.

---

### Post by Jason Cook on 2009-11-06
> **bodhi.zazen said:**
> 
To use ext2/3 you will need to install the windows drivers :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I will be using this on school's computers where I can't install drivers. I may install this on my windows computer. Thanks!

---

### Post by t0p on 2009-11-06
> **Jason Cook said:**
> I will be using this on school's computers where I can't install drivers. I may install this on my windows computer. Thanks!

I'd use ntfs format.  Both Ubuntu and Windows can read and write to ntfs without any need to install drivers.

---

