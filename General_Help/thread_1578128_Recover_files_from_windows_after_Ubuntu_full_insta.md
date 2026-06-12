---
title: "Recover files from windows after Ubuntu full instalation"
date: 2010-09-19
forum: General Help
---

### Post by danielswan18 on 2010-09-19
Guys, I just installed Ubuntu in full installation. But then my Windows 7 file went bye-bye. I tried to see if everything were really erased from my drive.

But then it showed that I'm still using 40G out of 250G of my disk. Why is it like that???.. can those file still be recovered???

Oh, and before I forget, my Windows 7 loader was actually erased.

Can I still install Windows 7 even if Ubuntu already used the whole drive???

and also, how can I delete partitions to make my HDD turn into a whole and single Drive before I install Windows 7???

---

### Post by bodhi.zazen on 2010-09-19
Depends on what you are needing to do here.

You can try testdisk.

I suggest you boot a live CD, testdisk is in the repos

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If testdisk does not find your missing partition, try photorec, it is part of test disk, or if the files are of any value, professional data recovery.

You did back up your data first I trust :twisted:

In terms of partition management, boot a live CD and use gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

In terms of installation and using the entire HD, go ahead an install and use the entire disk, no need to do anything but let the installer format the HD (applies to windows and Ubuntu).

---

