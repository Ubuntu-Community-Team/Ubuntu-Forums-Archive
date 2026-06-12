---
title: "Can Intellipark damage hard drives?"
date: 2011-02-12
forum: General Help
---

### Post by metalf8801 on 2011-02-12
I've found mix answers about whether or not intellipark can damage hard drives on systems running Ubuntu 10.04 and I hoping someone has better information than what I've found. 

From what I've read intellipark causes Western Digital Caviar Green hard drives (In this case a WD20EARS) to spin down ever 5 to 8 seconds and that Ubuntu, or just Linux in general, can cause the drive to spin up at the same time which can damage the drive. Is this really the case? 

Also Many post suggest using WDIDLE3, but my hard drive is not supported by WDIDLE3 according to [http://support.wdc.com/product/download.asp?groupid=609&sid=113](http://support.wdc.com/product/download.asp?groupid=609&sid=113) 

Is there anything I can do to prevent my hard drive from being damaged by intellipark or this not really a problem?

Thank you 
Dan

---

### Post by dcstar on 2011-02-13
> **metalf8801 said:**
> I've found mix answers about whether or not intellipark can damage hard drives on systems running Ubuntu 10.04 and I hoping someone has better information than what I've found. 

From what I've read intellipark causes Western Digital Caviar Green hard drives (In this case a WD20EARS) to spin down ever 5 to 8 seconds and that Ubuntu, or just Linux in general, can cause the drive to spin up at the same time which can damage the drive. Is this really the case? 
..........

Use the Disk Utility to see the Smart Attribute 4 count for the drive.

---

### Post by metalf8801 on 2011-02-13
> Use the Disk Utility to see the Smart Attribute 4 count for the drive.

I'm not sure if I fully understand what your saying. 
Here's what I'm trying to do 

I'm looking at the Disk Utility S.M.A.R.T. Data but I'm not sure what you mean by "Smart Attribute 4 count" 

Thank you
Dan

---

