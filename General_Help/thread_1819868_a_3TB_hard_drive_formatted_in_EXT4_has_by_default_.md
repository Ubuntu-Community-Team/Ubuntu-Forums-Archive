---
title: "a 3TB hard drive formatted in EXT4 has by default 139GB used"
date: 2011-08-06
forum: General Help
---

### Post by MockY on 2011-08-06
I am a little confused here. I bought a couple of 3TB drives and formatted them with Gparted to EXT4. Once done, the drive has 139.9GB used up space already.

Could someone care to explain why that is.

---

### Post by dcstar on 2011-08-06
> **MockY said:**
> I am a little confused here. I bought a couple of 3TB drives and formatted them with Gparted to EXT4. Once done, the drive has 139.9GB used up space already.

Could someone care to explain why that is.

If you do a search you will find many detailed explanations on why filesystems use disk space for their own purposes.

---

### Post by bodhi.zazen on 2011-08-06
> **dcstar said:**
> If you do a search you will find many detailed explanations on why filesystems use disk space for their own purposes.

That , and how much of the space is reserved for root ?

---

### Post by MockY on 2011-08-06
139.9GB just seem so excessive. 
Also, it usually does not show up as used space on the hard drive. It usually just decreases the total size of the hard drive and used space would still be 0.

Right now, a 3TB drive has 2.5TB of usable space.

---

### Post by papibe on 2011-08-06
As dcstar said it, there same space reserved.

Nevertheless, it may be possible to reduce that amount if the disk is just for data (no booting partitions). Check the section 'Modify Reserved Space (Optional)' in [this]("https://help.ubuntu.com/community/InstallingANewHardDrive") tutorial.

Regards.

---

### Post by MockY on 2011-08-06
tune2fs did the trick. Thank you.

---

