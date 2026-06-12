---
title: "How Do I Undo the Maverick Meerkat?"
date: 2010-09-13
forum: General Help
---

### Post by AaronStarr on 2010-09-13
How Do I Undo the Maverick Meerkat (Beta) Upgrade? Is that possible?

---

### Post by TeoBigusGeekus on 2010-09-13
I'm afraid not...

---

### Post by arpanaut on 2010-09-13
Backup your Data -> Reinstall previous OS

---

### Post by AaronStarr on 2010-09-13
If I have a dual boot install (with Winodws 7) all on one hard drive, how would I just do a fresh, default reinstall of ubuntu 10.04 without harming Windows 7?

---

### Post by Flyers2391 on 2010-09-13
> **AaronStarr said:**
> If I have a dual boot install (with Winodws 7) all on one hard drive, how would I just do a fresh, default reinstall of ubuntu 10.04 without harming Windows 7?

choose manual partition on install and choose your appropriate ubuntu partitions

---

### Post by Jazzy_Jeff on 2010-09-13
Just like you installed it the first time. Tell it to use your Ubuntu partition and overwrite it.

---

### Post by Rubi1200 on 2010-09-13
> **arpanaut said:**
> Backup your Data -> Reinstall previous OS
+1

Please make sure you backup before making any changes!

---

### Post by TeoBigusGeekus on 2010-09-13
Backup your /home folder (at least) on an external hd.
Boot up with the live cd and start the installation.
All the steps are straightforward, except maybe the partition manager:
Choose manual partitioning.
Assuming you have a separate /home partition, choose this as your new /home partition WITHOUT formatting it.
Choose your previous root partition (/) as your new root partition and you're done.
If you don't have a separate /home partition, I suggest you create one.
Be very careful not to touch any windows (ntfs) partitions.

---

### Post by arpanaut on 2010-09-13
All of the above is true unless you have installed through WUBI.
That's a whole other can of worms.

I don't know didly 'bout wubi.
Others around here do, Good Luck.

---

### Post by AaronStarr on 2010-09-13
Great. Thanks everybody. (And no, I didn't use WUBI).

---

