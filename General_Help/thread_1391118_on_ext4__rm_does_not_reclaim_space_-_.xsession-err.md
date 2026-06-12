---
title: "on ext4  rm does not reclaim space - .xsession-errors fills fs"
date: 2010-01-26
forum: General Help
---

### Post by zarthon on 2010-01-26
deleting a large file removes the file but df for example still reports 100% file system use until reboot. 
The space can't be reused!

Achemmm....
How do you reclaim space on an ext4 file system?

Rebooting works but clearly there must be another way!

The genesis of the problem is that .xsession-errors becomes enormous.
Over a certain size this log could use compression and annotate sequential repetitions and still remain useful.
I searched the forum and launchpad and the .xsession-errors issue is so 2007 but it's 2010 and i am running Karmic 9.10

---

