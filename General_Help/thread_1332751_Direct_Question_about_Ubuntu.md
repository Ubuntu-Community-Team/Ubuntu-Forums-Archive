---
title: "Direct Question about Ubuntu"
date: 2009-11-20
forum: General Help
---

### Post by wanderingarticfox on 2009-11-20
I have had very little luck in getting a response to my post so I will try a simplified approach in hopes of help.
   Do you have experience with 'Software RAID 1' in Linux {Ubuntu} ???
   Is it Stable when using RAID Hard Drives ????

---

### Post by Morphine Drip on 2009-11-20
works fine man. been using software raid for 5 years  1, 5, and 6

---

### Post by wanderingarticfox on 2009-11-21
Thank You for the reply, I really cannot afford a GOOD RAID Controller card at the time of my new build in April and really wanted to use this as an option other than the firmware RAID on the MOBO. I gues if you  have used it that long it is fairly stable and upgrades the kernel ok. Thx Again. Hopefully more people will report.

---

### Post by DeMus on 2009-11-21
> **wanderingarticfox said:**
> Thank You for the reply, I really cannot afford a GOOD RAID Controller card at the time of my new build in April and really wanted to use this as an option other than the firmware RAID on the MOBO. I gues if you  have used it that long it is fairly stable and upgrades the kernel ok. Thx Again. Hopefully more people will report.

I use a software RAID0. I do this since my stupid motherboard does not support it in any other way. RAID0 is not really a RAID since you have no way of keeping your data when things go wrong. I use it for the extra speed.
If I were you though I would use the firmware on your mobo.

---

### Post by wanderingarticfox on 2009-11-21
I thank you for your reply; however if when setting up the RAID 1 via mdadm and making both drives bootable via GRUB then I think that in theory you can 'cold' swap a drive to another system if it has the same BIOS settings in the SATA Controller of the MOBO.  See: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)   :D

---

