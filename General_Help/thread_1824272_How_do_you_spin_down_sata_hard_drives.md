---
title: "How do you spin down sata hard drives?"
date: 2011-08-13
forum: General Help
---

### Post by Keypel on 2011-08-13
(Ubuntu 10.10)

I went to System->Preferences->Power Management and checked spin down hard disks whet possible.

I have two internal sata hard drives. One is for the OS and the other is for media. 

Neither Hard disk is being spun down.

Is there something else I need to do?

---

### Post by Basher101 on 2011-08-13
Probably some background processes access them. Try to unmount the media one and see if it spins down then. And how are you even gonna tell if one spins down? the other one should make the same spin noise.

---

### Post by Keypel on 2011-08-13
Yes... The media one is/was completely unmounted.

Is there something else I need to change?

> And how are you even gonna tell if one spins down? the other one should make the same spin noise.

After a few hours, I check the smart status. I can tell it is still spinning because of the hard drive temp.

---

### Post by Basher101 on 2011-08-13
so far you musnt change anything. but how can you tell 100% sure if the disk stops spinning/spins down? i am pretty sure that the hdd case is not transparent...

---

### Post by Keypel on 2011-08-13
> but how can you tell 100% sure if the disk stops spinning/spins down? 

I'm not.

However common sense is telling me it is not spun down.  

First I unmount the sata drive that is used for media. Then I go to bed for 8 hours. When I wake up I go to Disk Utility and check the smart status. I can see the temp is 122 F.

I know that a drive that is spun down is cool to the touch.

However if you feel this is not sufficient evidence. I can remove the drive from the case and run a 12 inch sata cable. Then I will be able to feel the drive for vibration and heat.

---

### Post by Keypel on 2011-08-22
After pulling my hair out for weeks I found that upgrading hdparm to the newest version is what finally worked.

[http://packages.debian.org/squeeze/i386/hdparm/download](http://packages.debian.org/squeeze/i386/hdparm/download)

Went from hdparm 9.27 to 9.32.1

---

