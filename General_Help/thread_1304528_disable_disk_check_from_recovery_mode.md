---
title: "disable disk check from recovery mode"
date: 2009-10-29
forum: General Help
---

### Post by bpdp on 2009-10-29
Hi All,
Let me quickly explain what is going on. When I start my computer I get to a disk check. when the disk check gets to about 20% it re-boots. it will continue to loop like that until I hit the power button.

I'm kinda at a loss. I can get it to boot into recovery mode but I'm not sure how I can fix it from here. I'm wondering if there is a way that I can disable the disk check from recovery mode. I hope just to get in long enough to pull all the data off the hard drive. 

Thanks for any input.

---

### Post by az on 2009-10-29
> **bpdp said:**
> Hi All,

I'm kinda at a loss. I can get it to boot into recovery mode but I'm not sure how I can fix it from here. I'm wondering if there is a way that I can disable the disk check from recovery mode. I hope just to get in long enough to pull all the data off the hard drive. 

Thanks for any input.

The disk check should not cause a reboot.  Perhaps your computer is overheating?  

The best way to try to get your data is to run the live cd.  If you do have hardware problems, that will reveal itself while you are running the live cd.  If you can run fine int he live cd, then perhaps you have disk problems which is causing you to run into trouble.  Try to copy the important data while in the live session.

---

### Post by alphaniner on 2009-10-29
My advice would be to check the disk manually.  But you shouldn't do that when it's mounted.  Can you tell what disk is being checked?  And what is the output of **mount** when you boot into recovery mode?

---

### Post by zika on 2009-10-29
> **bpdp said:**
> Hi All,
Let me quickly explain what is going on. When I start my computer I get to a disk check. when the disk check gets to about 20% it re-boots. it will continue to loop like that until I hit the power button.

I'm kinda at a loss. I can get it to boot into recovery mode but I'm not sure how I can fix it from here. I'm wondering if there is a way that I can disable the disk check from recovery mode. I hope just to get in long enough to pull all the data off the hard drive. 

Thanks for any input.You might try to change line in Your /etc/fstab with Your boot partition to have 0 0 a the end if it has 0 1.

---

