---
title: "ubuntu not saving my data changes in windows 7"
date: 2011-03-03
forum: General Help
---

### Post by Prakash Joshi on 2011-03-03
hi 
i have installed windows 7 and ubuntu karmic kola 
then i upgraded to 10.04
now when i m making any changes to my data present on hdd then the changes like creating new folder saving any data transferring data from one location to other are not reflected to windows 7
what would be the problem please help
and what is FOUND.000 folder..

---

### Post by Mark Phelps on 2011-03-03
You didn't say where in the Win7 filesystem you're making the changes, but if they are to files in your Win7 OS partition, my advice is -- stop doing that.

Making changes inside the Win7 OS partition from Ubuntu is asking for trouble in Win7.

There have been lots of reports here of files vanishing and of Win7 no longer booting as a result.

A much better solution, if you have less than 4 primary partitions, is to do the following:
1) Use the Win7 Disk Management utility to shrink the Win7 OS
2) Create an NTFS data partition in the unallocated space
3) Put shared data files into that partition.

---

### Post by Megaptera on 2011-03-03
... and here's a tutorial to take you through what MarkPhelps suggested:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

worked well for me.

---

