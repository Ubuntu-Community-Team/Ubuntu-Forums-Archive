---
title: "Software RAID with hdparm Power Savings"
date: 2011-07-27
forum: General Help
---

### Post by Kissell on 2011-07-27
Well, I have a 10 disk software raid-6 put together with mdadm, and I edited the hdparm file so that each of the ten disks would spindown after twenty minutes of inactivity.

Worked great...  the file server is mostly archival, it only gets accessed a few times a day, from a windows client via a samba share, and then it takes a few seconds the first time to show the files, but after that it is fine.

Until yesterday, while I was trying to access the files, it evidently couldn't wake up all ten disks quick enough, so the software raid claimed two disks had failed and it removed them from the array.  Oh no!!  I was no longer redundant...  

I added the disks back to the array, and removed the hdparm settings about putting them to sleep.  Ideally I would like them to sleep...  anyone have experience with this problem?

I'm still using Ubuntu 10.10...  hated how the unpolished unity changed things like from the terminal I couldn't do ALT-E <ENTER> anymore to paste what was in my clipboard, so waiting for 11.10 to come out before I upgrade, but I did already manually upgrade to the latest mdadm.

---

