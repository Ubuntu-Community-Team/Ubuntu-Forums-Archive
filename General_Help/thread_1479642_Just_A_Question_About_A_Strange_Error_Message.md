---
title: "Just A Question About A Strange Error Message"
date: 2010-05-10
forum: General Help
---

### Post by cain071546 on 2010-05-10
after upgrading my Ubuntu Hardy to Lucid on reboot every time i get a Quick little error message saying that THE DRIVE FOR UUID blah blah IS NOT PRESENT OR IS NOT READY and then it gives a option for recovery. It is so fleeting i cant catch all it says but it boots past it after like 2and1/2 seconds but it does slow down the boot time by like 8 maybe 10 seconds all together and is the only issue with the system I know that UUIDs are used to identify drives 
and i am wondering if having my 40g partitioned into 12GsXP/15GsUbuntu and a 13G extra ext4 and a 691Mb swap might have something to do with it

---

### Post by dcstar on 2010-05-11
> **cain071546 said:**
> after upgrading my Ubuntu Hardy to Lucid on reboot every time i get a Quick little error message saying that THE DRIVE FOR UUID blah blah IS NOT PRESENT OR IS NOT READY and then it gives a option for recovery. It is so fleeting i cant catch all it says but it boots past it after like 2and1/2 seconds but it does slow down the boot time by like 8 maybe 10 seconds all together and is the only issue with the system I know that UUIDs are used to identify drives 
and i am wondering if having my 40g partitioned into 12GsXP/15GsUbuntu and a 13G extra ext4 and a 691Mb swap might have something to do with it

You probably have an old /etc/fstab entry that is no longer valid.

---

