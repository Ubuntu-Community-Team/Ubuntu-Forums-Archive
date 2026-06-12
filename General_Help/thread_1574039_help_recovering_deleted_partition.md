---
title: "help recovering deleted partition"
date: 2010-09-13
forum: General Help
---

### Post by ibrabeicker on 2010-09-13
I screwed up really bad when trying to create a bootable usp, on the Startup disk creator I accidentaly erase my external HD that had 2 partitions, 1 is a trash ext3 and the other one is a 466GB ntfs partition that contained all my backups form the last 1 year.

Any one have a good tool that work on this? Paragon rescue kit "undelete partition" didn't work

thanks

](*,)](*,)](*,)](*,)](*,)

---

### Post by Rubi1200 on 2010-09-13
Take a look here for possible solutions:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by baddnady23 on 2010-09-13
Depending on what was done, I have seen people have success with **testdisk**.  My experience is very limited with it so I couldn't walk you through it.  That'll be for someone else to do.  I'd recommend not using the disk for anything until you attempt to recover your lost data. :-k

---

### Post by ibrabeicker on 2010-09-14
SOLVED

the tutorial didn't help, those programs don't have an graphic interface and after running for 2 hours parted didn't recognize a 100GB partition, and found a bunch of other partitions that had nothing but .Trash-bin

I've found a great program called [power data recovery]("http://www.powerdatarecovery.com/") and it ran for 30 minutes before finding all my files

---

