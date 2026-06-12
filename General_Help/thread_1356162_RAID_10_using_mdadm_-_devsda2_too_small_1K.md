---
title: "RAID 10 using mdadm - /dev/sda2 too small: 1K"
date: 2009-12-15
forum: General Help
---

### Post by shelzmike on 2009-12-15
I am attempting a fresh install on our old server of Ubuntu desktop (most recent version). I am attempting to set up RAID 10 (software) and found a pretty good tutorial here: 
[http://www.howtoforge.org/install-ubuntu-with-software-raid-10](http://www.howtoforge.org/install-ubuntu-with-software-raid-10)

I have followed all instructions and have successfully made it to the first mdadm command of:

```
mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sda2 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

when I get an error. 

The error says:
/dev/sda2 too small: 1K

and then exits. I have no idea what the problem is as it is not very descriptive. The size of the sda2 is 130000MB and is exactly the same size as as the other 4 sdb1, sdc1, and sdd1

As a little back story, this server used to have hardware RAID 10 set up on it. I wanted to use software RAID instead, so I just changed the SATA in bios from RAID to IDE, which makes it a JBOD set up for the moment, right?

Could it be something to do with the way the first disk had been formatted before? Do I need to completely wipe this drive before I move on? I was getting errors using cfdisk on HDDs 3 and 4. I had to use gparted to create and then I was able to use cfdisk regularly. Thanks.

Mike

---

### Post by Joffer on 2010-03-17
Did u ever figure this out? Have kinda the same error trying to make a raid-1

---

### Post by prodigy_ on 2010-03-17
A possible [solution](http://www.opensubscriber.com/message/linux-raid@vger.kernel.org/7775400.html).

---

