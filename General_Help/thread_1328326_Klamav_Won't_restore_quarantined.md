---
title: "Klamav Won't restore quarantined"
date: 2009-11-16
forum: General Help
---

### Post by mach102 on 2009-11-16
I installed klamav and did a scan. I didn't realise auto quarantine was enabled and also my windows partition was mounted.

Now I have a ton of windows program files and program executables in quarantine because they are encrypted zips or broken executables..

I can't get klamav to restore any of the files on the windows partition.

I'm a noob to linux. this is what the error says:

There was a problem restoring /media/disk/WINDOWS/system32/drivers/update.sys. Check your diskspace, the permissions on the location you are restoring to, and whether a file with the same name already exists in that location. 

I'm pretty sure it has to do with write permission, but I can't figure it out. If klamav could remove the file, why can't it put it back?

Please help


ETA: I want to unistall karmic and go back to 9.04, but Klamav has a lot of widows files quarantined so i want to restore those before I repartition the ubuntu partition back to 9.04. 9.10 is nothing but problems for me.

ETA2: I tried: sudo klamav      to run klamav in root and I changed the permissions for one of the folders that I need to restore to and still doesn't work

ETA3: Solved. The mount point for the partition was different than what klamav had recorded. So I remounted specifying the old mount point / name and then it worked fine.

---

### Post by LGommans on 2010-05-09
removed

---

