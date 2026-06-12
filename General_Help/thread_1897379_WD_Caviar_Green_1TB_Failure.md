---
title: "WD Caviar Green 1TB Failure"
date: 2011-12-19
forum: General Help
---

### Post by tobiz on 2011-12-19
I've been trying to set up a RAID-1 array on ubuntu 11.10 (64-bit) using 2 (new) WD Caviar Green 1TB disks. After creating the RAID array the sdb disk always fails (the array uses sdb & sdc) and goes into degraded mode. I've tried running the extended SMARTCtrl tests on both disks and both fail at LBA 566231424 as the first error. The disks were bought at the same time and hence probably come from the same manufacturing batch. I've tried swapping SATA ports on the m/b, running the SMARTCtrl tests with only 1 disk connected etc., but the result is always the same. The supplier is willing to test the disks themselves and replace them if faulty.  However before returning them I'd like to eliminate as many possibilities as I can.  Question: are the disks really faulty or is there some other problem that makes them appear faulty?

---

### Post by Mark Phelps on 2011-12-19
I had a recently bought WD 2TB Green go bad on me after only a few months.

You can go to the WD site and download a utility that can then be used to scan your drive for faults.  But, I think it only runs in Windows.

---

### Post by seawolf167 on 2011-12-19
> **Mark Phelps said:**
> You can go to the WD site and download a utility that can then be used to scan your drive for faults.  But, I think it only runs in Windows.

Aye - Windows only. The [download is here ]("http://support.wdc.com/product/download.asp?groupid=607&sid=3&lang=en")(it is the same for all the products).

If you can get access to a Windows box, run it and have it check your drive. Unfortunately, [running it in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5497") doesn't work so well :(

---

### Post by lukeiamyourfather on 2011-12-19
Some of the new large capacity drives use 4 kilobyte sectors instead of 512 byte sectors. Not all hardware (or operating systems) support the feature. I think recent Linux distributions like Ubuntu support it but I haven't tried it personally. If you have access to another machine or another operating system that might help determine if the problem is with the disks or with the machine.

---

