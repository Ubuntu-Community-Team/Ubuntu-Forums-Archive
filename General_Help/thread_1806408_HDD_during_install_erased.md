---
title: "HDD during install erased ?"
date: 2011-07-17
forum: General Help
---

### Post by ThatAngryperson on 2011-07-17
So, i just wanted to install Ubuntu alongside Windows 7 to check it out.
I just checked the to install it alongside Windows ( had some partitions free )
The installation Progress went good till the end, when it reported an error with the cd.

As i reentered Windows i soon had to realize that the Installer seemed to automatically used my second HDD as its destination.
Which is really bad. 400 Gb data erased. Without asking.
I cant uderstand why it just would overwrite an Partition in use.
My question now is, if there is any chance, that i could restore that lost data ?

Thanks in advance.

---

### Post by ajgreeny on 2011-07-17
Using your ubuntu live CD please run **system ->administration ->gparted** and attach screenshots of your disks back here.  Also it may help to see the output of ```
sudo fdisk -l
``` in terminal.

---

### Post by ThatAngryperson on 2011-07-17
thanks for the tipp, saddly i reformated the disk as soon as i saw the change of the filesystem.

will try later again with ubuntu.

thanks

---

