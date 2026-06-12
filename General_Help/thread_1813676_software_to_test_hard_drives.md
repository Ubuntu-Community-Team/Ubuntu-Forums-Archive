---
title: "software to test hard drives"
date: 2011-07-28
forum: General Help
---

### Post by chedderslam on 2011-07-28
I am a bit new to ubuntu.  I have a couple of older ide hdds that I would like to use, but I think a couple of them might be going bad.  Can anyone recommend software that I can use to test the drives thoroughly?  Thank you.

---

### Post by Wayne_V on 2011-07-28
I would recommend a badblocks test with write (assuming there is nothing on the drive now):

sudo badblocks -wsv /dev/sd<X>

Then, use "smartctl -a /dev/sd<X>" to see what the drive reports.

---

### Post by chedderslam on 2011-07-28
Thank you very much.

---

