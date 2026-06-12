---
title: "Recover ext4 after wrongly converting it to ntfs"
date: 2011-06-29
forum: General Help
---

### Post by fabsen82 on 2011-06-29
hey guys,

i did the following dumb thing: not exactly knowing what i was doing, i wanted to change the format of my backup drive from ext4 to ntfs. what i thought would be possible without erasing the data, was simply done by formating the drive. but because this took only 6 sec, i have still hope that my data was not completely destroyed. 

now the question is: are there any possibilities that i get my data back? i unmounted the drive afterwards and did not write anything to it.

any suggestions welcome,

fabian

---

### Post by pjd99 on 2011-06-29
I may not be 100% on this, but a quick format sets up the partition to order data in a certain way. While your data itself is still there, the information that describes the file system (the locations of files, i.e. which parts of the physical hard disk those files are kept) is now missing. A lot of the raw information will still be there, some may be corrupted from the format. You might get lucky with some data recovery tools, or you could pay to get it recovered (very expensive, in terms of $ per file/MB) if the data can't be recovered via conventional means (backups, sourcing it from the net etc) and you really, really need it back.

There are tools that can attempt data recovery in a non destructive way, I recently tried **foremost** to attempt to recover some accidentally deleted files (shift-deleted when the wrong windows was in focus) without much success, so I don't rate your chances too highly given that you've given it a different file system to contend with. :(

Maybe some else here can offer more hope...

EDIT: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Might be of some use.

---

### Post by Rodney9 on 2011-06-29
SpinRite - [http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

> If SpinRite is not used until after a crash, it skillfully picks up all the pieces, recovers your data, and puts everything back together again. 

---

