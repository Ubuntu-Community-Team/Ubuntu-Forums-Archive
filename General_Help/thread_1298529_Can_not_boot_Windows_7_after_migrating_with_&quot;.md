---
title: "Can not boot Windows 7 after migrating with &quot;dd&quot;"
date: 2009-10-22
forum: General Help
---

### Post by dandandan on 2009-10-22
Hi guys

Since my syshdd was about to fail i migrated my windows 7 and ubuntu (karmic) installation to another hdd with dd.

I moved both Windows partitions (main one and the System reserved) and i can mount both of em cleanly under ubuntu which boots fine after the migration.

The Problem is, Windows 7 will not boot anymore, after "Starting up"
 nothing else happens.

Does anyone have any clue about this?

My grub entry is the following:
(worked perfectly before)

title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1


-dan

---

### Post by oldfred on 2009-10-23
Herman says that windows is designed to check if it has been cloned and prevents it from booting:
[http://ubuntuforums.org/showpost.php?p=8139151&postcount=6](http://ubuntuforums.org/showpost.php?p=8139151&postcount=6)

You could try all the windows repairs and see if any help from a windows recovery disk.

This site also now has a win7 recovery
If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Vista will not repair XP(they create the boot sectors differently)

---

