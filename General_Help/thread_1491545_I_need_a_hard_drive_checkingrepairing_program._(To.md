---
title: "I need a hard drive checking/repairing program. (To check two new hard drives.)"
date: 2010-05-23
forum: General Help
---

### Post by TheOnlyMrK on 2010-05-23
About a month ago I built a new computer (see signature) and so far it's been working perfectly fine without a single problem, but after awhile I started to worry since I never actually tested the two hard drives I bought for it and instead just put all my stuff on them and erased my old hard drive not having a backup or anything. So I was wondering what is a good hard drive checking program that I could use to make sure the hard drives are okay?

EDIT: I should of put more detail in my post. I need something that actually scans the surface of the hard drive for bad sectors not just check the filesystem on the hard drive, it needs to be free, and it needs to either work on Ubuntu and/or Windows or have it's own LiveCD.

---

### Post by uRock on 2010-05-23
Go to System> Administration> Disk Utility. That tests the hard drive and reports the status of it.

System> Administration> System Testing also checks the HDD.

---

### Post by TheOnlyMrK on 2010-05-23
> **uRock said:**
> Go to System> Administration> Disk Utility. That tests the hard drive and reports the status of it.

System> Administration> System Testing also checks the HDD.
I would use that but it only checks the filesystem on the hard drive, I need something that actually scans the hard drive surface (like Windows 95/98/ME ScanDisk in "Thorough" mode)

---

### Post by tahitiwibble on 2010-05-23
Someone suggested this a couple of days ago and I'm thinking of getting a copy myself. [http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

---

### Post by quadproc on 2010-05-23
> **TheOnlyMrK said:**
> About a month ago I built a new computer (see signature) and so far it's been working perfectly fine without a single problem, but after awhile I started to worry since I never actually tested the two hard drives I bought for it and instead just put all my stuff on them and erased my old hard drive not having a backup or anything. So I was wondering what is a good hard drive checking program that I could use to make sure the hard drives are okay?
This doesn't exactly answer your question but you may be able to ask the drives themselves to report on themselves.  Many new disks have SMART capability and you can use the smartctl program to access this and get a report.

Please note that Ubuntu version 9.10 had disabled this capability because the smartctl program could damage some flash drives.  If you want to re-enable it then you need a trivial one line patch.

quadproc

---

### Post by uRock on 2010-05-23
Disk Utility checks SMART. I am not sure how strong the scan is with the System Testing function, but I know it does test the drive.

---

### Post by James78 on 2010-05-23
Best I can give you is badblocks. It's in the e2fsprogs in case you need to get it.```
sudo badblocks /dev/sda
```It'll just print out a list of badblocks, so if it returns nothing, you're good to go.

---

