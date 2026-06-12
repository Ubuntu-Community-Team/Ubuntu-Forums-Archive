---
title: "clonezilla smaller target part. &amp; MBR"
date: 2011-04-13
forum: General Help
---

### Post by ahso4271 on 2011-04-13
Hi
how to clone a partition to a smaller partition in clonezilla? 
Didn't see a -c option only -r
Also i want to backup the mbr together with the hfs+ filesystem part.
Thanks Michael

---

### Post by Mark Phelps on 2011-04-13
This has been asked several times, and from my experience, and everything I've seen, you can NOT use Clonezilla to clone to a smaller partition size; you have to shrink your original partition first.

---

### Post by seawolf167 on 2011-04-13
> **Mark Phelps said:**
> This has been asked several times, and from my experience, and everything I've seen, you can NOT use Clonezilla to clone to a smaller partition size; you have to shrink your original partition first.

Yup, this is how I've always done it when needed. Shrink the source partition so it is less than or equal to the target partition size, then image that partition only and restore to the target drive

---

### Post by ahso4271 on 2011-04-15
ok cloned to a bigger partition. but after cloning it back i cannot boot. also partition names were changed.
am i doing something wrong??
Thansk
Michael

---

### Post by seawolf167 on 2011-04-15
Take a look at the instructions here - GRUB is probably just pointing to the wrong partition. Once you change that you'll be good to go.

Notice where it says

```
set root=(hd0,1)
linux /vmlinuz root=/dev/sdXY
```in the picture, you'll want to set that to your correct Ubuntu partition, maybe (hd1,3); (sda,1) or whatever it is. If you fire up the LiveCD, open a terminal and type

```
sudo fdisk -l
```You can see what/where your root partition is

---

