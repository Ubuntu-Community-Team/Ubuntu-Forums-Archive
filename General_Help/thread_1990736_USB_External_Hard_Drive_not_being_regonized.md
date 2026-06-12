---
title: "USB External Hard Drive not being regonized"
date: 2012-05-29
forum: General Help
---

### Post by rebuhjc on 2012-05-29
Hi.
I Just installed Ubuntu 8.04 LTS on my dell dimension 3000. While trying to plug my external HD in, i noticed it was not being regonized. This was very strange considering when i reinstalled the "installer" regonized it as a install location. it is formate in the format exFat. Any help would be greatly appriciated!

Thanks!

---

### Post by efflandt on 2012-05-29
8.04 is a very old Ubuntu version that has not been supported for quite some time, so you would not even be able to get any updates for it.  The oldest version of Ubuntu I have used was 9.04 a week before 9.10 was released, and current version is 12.04

When you connect the USB drive, in a terminal (xterm) what does the end of **dmesg** show about the USB drive, if anything?

---

### Post by Balyasin on 2012-05-30
There is obviously a lot to know about this. I think you made some good points in Features also. Keep working, great job!

---

### Post by haqking on 2012-05-31
> **efflandt said:**
> 8.04 is a very old Ubuntu version that has not been supported for quite some time, so you would not even be able to get any updates for it.  The oldest version of Ubuntu I have used was 9.04 a week before 9.10 was released, and current version is 12.04

When you connect the USB drive, in a terminal (xterm) what does the end of **dmesg** show about the USB drive, if anything?

8.04 LTS if its server is supported until April 2013

---

### Post by rebuhjc on 2012-05-31
> **efflandt said:**
> 8.04 is a very old Ubuntu version that has not been supported for quite some time, so you would not even be able to get any updates for it.  The oldest version of Ubuntu I have used was 9.04 a week before 9.10 was released, and current version is 12.04

When you connect the USB drive, in a terminal (xterm) what does the end of **dmesg** show about the USB drive, if anything?

nothing at all...

---

### Post by rebuhjc on 2012-06-01
> **rebuhjc said:**
> nothing at all...

After much help from everyone i updated to 12.04. I then used a couple of commands to mount the HD, as ubuntu does not recognize exfat. its now up and running! 

Thanks!:popcorn:

---

### Post by haqking on 2012-06-01
> **rebuhjc said:**
> After much help from everyone i updated to 12.04. I then used a couple of commands to mount the HD, as ubuntu does not recognize exfat. its now up and running! 

Thanks!:popcorn:

Cool glad you got it sorted, remember to use thread tools to mark this thread as solved.

Cheers

---

