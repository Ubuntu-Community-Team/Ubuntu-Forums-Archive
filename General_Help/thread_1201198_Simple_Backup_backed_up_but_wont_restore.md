---
title: "Simple Backup backed up but wont restore"
date: 2009-06-30
forum: General Help
---

### Post by lordadi on 2009-06-30
Hi all,


I recently backed up my dad's computer with SBackup onto the external HDD I have. Now that the time has come to restore it, I'm having major issues described below

[LIST=1]
[*]When I start the restore, it shows me that the restore has started and "may take some time". However, after 16 hours, nothing has happened (only about a 10th of the files have been restored)
[*]This restore is to the /home/ partition. Thinking that there may be some permissions issues, I told it to restore to /home/usr/OLD/. This did not help.
[*]After a while of the restore, the external HDD's bridge light turns off as if the disk is off (but it is actually on, I can feel the HDD spinning). Simultaneously, the external HDD gets unmounted.
[/LIST]

So now my dad has no usable computer and I'm tearing my hair out. Any ideas what's going on? How can it be fixed?

Help please!

Lordadi.

---

### Post by lordadi on 2009-07-05
After banging my head against a wall, I realized what I was doing wrong (or not doing right). 

When you ask SBackup to restore, it has to read all the contents of the files.tgz archive. In my case this was a healthy ~70 GB. When I tried to do it manually, the archive manager began a lengthy process of reading files in the archive. This is exactly what SBackup was doing and it took ~30 hours for it restore the data.

So the lesson is: patience pays off. Unless of course, you never screw a HDD up, in which case it has no use ;)

---

