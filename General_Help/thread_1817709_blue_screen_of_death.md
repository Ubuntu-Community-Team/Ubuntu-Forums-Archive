---
title: "blue screen of death"
date: 2011-08-03
forum: General Help
---

### Post by Vertigo841 on 2011-08-03
Hello all, 

 I am entirely new to the ubuntu os but am loving what I've found. I am currently attempting to install this os permanently (currently running off a live disc) but  am running into a complication. My laptop was previously running windows xp and i was graced by a BSoD with the message: 

STOP: c0000218 {Registry File Failure} The registry cannot load the hive (file): \Systemroot\System32\Config\SOFTWARE or its log or alternate. It is corrupt, absent, or not writable.

I have researched how to fix this and, on the surface, seems to be a simple fix. pop in the recovery disc, enter the recovery console and type out a few simple commands. when i attempted this i was greeted with an access denied message. I would just reinstall the win os then switch to this one but i have some valuable data which i stand to lose if i perform said re-installation. I would just pull the data off the hd but since its efs encrypted they would be pretty useless.

How do i gain permission to modify the corrupted file, retrieve my information and finally be done with windows for good?

---

### Post by WorMzy on 2011-08-03
If you're getting a BSoD, then you're not booted into the Ubuntu Live CD. Check the boot order in your BIOS settings, and make sure that you're booting from the CD, not hard disk.

Once booted into the liveCD for real, you should be able to mount your Windows partition, then copy the files you need to keep over to a USB stick. Then just run the Ubuntu installer, and tell it to use the whole disk. Any data left on the hard disk will be erased, and Ubuntu will be installed over the top of it.

---

### Post by Mark Phelps on 2011-08-03
I think the following might pose some problems in simply accessing the drive data:

> I would just pull the data off the hd but since its efs encrypted they would be pretty useless.

So, if the whole drive is encrypted, then there's simply no way to access the data.

---

### Post by WorMzy on 2011-08-03
I missed that part.

In that case, you should try asking on a Windows forum.

---

