---
title: "Cannot format External Hard Drive. Why?"
date: 2011-08-10
forum: General Help
---

### Post by Wizgot on 2011-08-10
This is a little long so bear with me please. I wanted to get started with Ubuntu so I partitioned an external hard drive with Ubuntu 11.04 onto it. After finding out my computer couldn't but up from a external hard drive I wanted to format my drive. When I plugged it into my computer, Windows would not recognize it. I then dual booted Ubuntu 11.04 onto my laptop and attached my drive. Ubuntu found it a recognized it as 3 separate disks. I then opened up disk utility and told it to format the drive. After clicking a couple "OKs" I got an error message: An error occured while performing an operation on "500 GB Hard Disk" (Seagate FreeAgent GoFlex): The device is busy I clicked details and got:One or more partitions are busy on /dev/sdb. I was wondering what I could do since it isn't doing anything in the first place. I just want to format the whole thing. I'm not computer specialist but if someone knows an override I can punch into terminal I would really appreciate it.:D

---

### Post by Synoc on 2011-08-10
first, have you tried formatting it in Windows? I hate asking someone to use Windows, but as a diagnostic tool it might help. The problem isn't one I'm familiar with. but I'll help where I can. I can ask Mr Google for help.

---

### Post by deserthowler on 2011-08-10
Did you remove the existing partitions first?
Earl

---

### Post by Wizgot on 2011-08-10
I figured it out. I had to unmount all the partitions before I could format the drive. Problem solved.

---

