---
title: "Palimpsest says bad sectors- how to fix them?"
date: 2009-11-05
forum: General Help
---

### Post by myromance123 on 2009-11-05
I am not sure where to post this thus I post it here.
Forgive me moderators if this is the wrong place.

My issue here is that I have a WD HDD (Western Digital External Harddisk) size 640GB. I partitioned it into 2 partitions in Window$ Vista and ever since my Laptop has not been able to read it unless I do it through the terminal. This is not the case for my Desktop.

The thing here is that Palimpsest Disk Utility (since 9.10) has started complaining that my HDD has a whole lot of bad sectors, BUT it doesn't tell me HOW to fix it....

 I can't seem to find anything from Google (maybe wrong keywords, cant think what it might be?).

How can I "fix" these "bad sectors" if they are really bad sectors?
I checked with Vista and it says nothing of the sort.
The HDD was originally FAT32 but I changed it to NTFS when I added a partition.

*On another note, does Ubuntu need defragmenting? Is there even a way? These two things I can't find anything relevant from Google.

---

### Post by alphaniner on 2009-11-05
Please copy the text or post a screenshot of Palimpsest showing the details of the failure.  For example:

> REALLOCATED SECTOR COUNT - Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area)

ASSESSMENT
Warning

VALUE
Normalized: 100
Worst: 100
Threshold: 5
Value: 8848628 sectors

It may be a bug, but we need to know exactly what Palimpsest is reporting.

---

### Post by myromance123 on 2009-11-05
Here's a snapshot

---

### Post by alphaniner on 2009-11-05
The problem is probably real and not caused by a bug.  The bug causes absurd numbers (like in my post, 'Value: 8848628 sectors').  I recommend you test your drive with Western Digital's diagnostic tool which you can get [here]("http://support.wdc.com/product/download.asp?modelno=wd6400aacs&x=17&y=18").  It may be able to remap the bad sectors.  Choose one of the 'for DOS' versions, they are bootable.

---

### Post by myromance123 on 2009-11-05
So there is no tool in Ubuntu or Linux to solve this type of problem?

Fixing bad sectors through Vista is also useless?

I'll test the DOS solution tomorrow as tonight I am too tired.

Thanks for helping me.

If anyone knows of a Linux tool/software that can do this I'd prefer that.

---

### Post by oktapod on 2009-11-07
I have different problem.

My BIOS has more than 1 years that alerts me before boot with 
"s.m.a.r.t. status bad backup and replace" but I never considered it.
I had bad sector experience before (not with my HDD) and resolved it with HDD REGENERATOR that I would suggested to use, to myromance123.

Palimpsest seems to be a good utility but would be better to have the solution to.

If someone has more info or even the solution please help.

Thanks in advance.

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healty'

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healty'

---

