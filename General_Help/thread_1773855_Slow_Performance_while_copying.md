---
title: "Slow Performance while copying"
date: 2011-06-02
forum: General Help
---

### Post by margemoosh on 2011-06-02
in ubuntu when i start to copy files system responses gets slow and most of cpu time is in wait state is there anyway to change priority of copy and let system work smooth while copying?

---

### Post by LowSky on 2011-06-02
Can we have more details: Your computer specs, what you are coping files from and to. what other tasks are you doing. Large files being copied toa flash drive can take a very long time based on what class the flash drive is rated. Some low end models can be extremely slow. Also if you are moving very large files your PC need to cache them especially if you are cutting and pasting.

---

### Post by margemoosh on 2011-06-02
> **LowSky said:**
> Can we have more details: Your computer specs, what you are coping files from and to. what other tasks are you doing. Large files being copied toa flash drive can take a very long time based on what class the flash drive is rated. Some low end models can be extremely slow. Also if you are moving very large files your PC need to cache them especially if you are cutting and pasting.

i have a turion64 x2 cpu with 2 gb ram
i'm moving files from ntfs drive on my laptop to an external hard disk(ntfs) using usb2.
my problem is not slow copy speed my problem is i can't do anything with laptop while copying using top i found that mountfs using most of my cpu time.
using renice and give mounfs a low priority will make my system smooth?

---

