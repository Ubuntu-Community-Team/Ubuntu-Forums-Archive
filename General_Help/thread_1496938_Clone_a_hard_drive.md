---
title: "Clone a hard drive"
date: 2010-05-29
forum: General Help
---

### Post by ubudog on 2010-05-29
How do I do this in Ubuntu?

---

### Post by lmarmisa on 2010-05-29
Try Clonezilla:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by BoneKracker on 2010-05-29
```
dd if=/dev/foo of=/dev/bar
```

(If either disk isn't using a blocksize of 512, see the dd man page for options bs, ibs, obs to set the block size accordingly.)

Warning: dd will do exactly what you tell it to, without making any attempts to gauge the sanity of the act.  Read the documentation.

---

### Post by lmarmisa on 2010-05-29
> **BoneKracker said:**
> ```
dd if=/dev/foo of=/dev/bar
```(If either disk isn't using a blocksize of 512, see the dd man page for options bs, ibs, obs to set the block size accordingly.)

Warning: dd will do exactly what you tell it to, without making any attempts to gauge the sanity of the act.  Read the documentation.

VERY IMPORTANT: source and destination drives have to be UNMOUNTED!!!

In order to try to avoid possible errors in disks, I suggest this slightly modified command:

> 
dd if=/dev/source of=/dev/destination conv=noerror,sync
dd uses a force brute method. Clonezilla is able to do a smarter cloning and spends only a fraction of the time.

---

### Post by BoneKracker on 2010-05-29
> **lmarmisa said:**
> VERY IMPORTANT: source and destination drives have to be UNMOUNTED!!!

In order to try to avoid possible errors in disks, I suggest this slightly modified command:

dd uses a force brute method. Clonezilla is able to do a smarter cloning and spends only a fraction of the time.

If it's only copying the used blocks; that's not a true image of the disk.  That's not really "cloning" the disk, just the data.  Also, you can pipe dd through compression and decompression, which achieves much of the same effect without violating the true integrity of the disk image.

But I suppose, if you are "cloning" data every day or something, and you don't really need a true disk image per se, then installing another application on your system just for that purpose alone might make sense.  Also, dd is kind of dangerous, so something that does some sanity checks might be valuable to many.

---

### Post by ubudog on 2010-05-30
Thanks for your responses!

---

