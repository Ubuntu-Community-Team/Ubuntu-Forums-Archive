---
title: "rdiff-backup commandline"
date: 2012-09-15
forum: General Help
---

### Post by eslavko on 2012-09-15
Hello...

Does someone know how to join this backup to single command?

rdiff-backup /media/HW_WIN/00_Proj       /media/SlavkoBKP/RDIFF-CAA/00_Proj
rdiff-backup /media/HW_WIN/88_Internet/  /media/SlavkoBKP/RDIFF-CAA/88_Internet

I can't figure how to manage --include option..

---

### Post by Roasted on 2013-02-05
Hello! Have you had any luck with this? I too am trying to figure out how to work with the include option. With rsync, it's braindead easy, but with rdiff-backup I'm finding it beyond confusing. I've exhausted so many Google tips but so far, I'm still getting fatal errors when I run this. My best bet so far is just rdiff'ing everything, as that works, but it's not the end goal.

---

### Post by eslavko on 2013-02-06
The only way I find is via include file list. But in the end I use separate backup as one folder is done more frequently as other.

---

