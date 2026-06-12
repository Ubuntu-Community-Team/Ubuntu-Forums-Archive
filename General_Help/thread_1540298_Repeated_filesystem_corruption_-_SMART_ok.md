---
title: "Repeated filesystem corruption - SMART ok"
date: 2010-07-27
forum: General Help
---

### Post by merike on 2010-07-27
A Xubuntu 9.10 based system has started to get filesystem corruption rather frequently forcing me to run fsck roughly every other boot. SMART check for hard drive is ok and memory too. What else could possibly cause it? Something to check, try?

This is 8 years old system, would motherboard starting to die cause something like this?

---

### Post by dabl on 2010-07-27
If SMART says the hard drive is OK, it is possible that the controller/interface on the motherboard is starting to fail.

What is the filesystem/format?

---

### Post by merike on 2010-07-27
> **dabl said:**
> What is the filesystem/format?
ext3

---

### Post by dabl on 2010-07-27
OK, ext3 is fine.

I would be nervous about the hardware.  With an 8-year old motherboard, I suppose the hdd technology is IDE.  Even though SMART is giving you happy news, something is starting to cause problems, and it is surely in the hardware side of things -- there's no reason Xubuntu Linux 9.10 should have such a problem.  I would be planning a major backup of my data, in advance of changing hardware.

p.s. make sure the data cable/connector is tight on both the motherboard and the hard drive.  You could replace it very cheaply, just in case that is the problem.

---

