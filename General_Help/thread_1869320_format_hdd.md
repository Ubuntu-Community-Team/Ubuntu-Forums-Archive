---
title: "format hdd"
date: 2011-10-25
forum: General Help
---

### Post by itsferny09 on 2011-10-25
i am looking to format my hard drive on my toshiba laptop in order to boot win xp
how do it reformat a hard drive using the live cd?
i am currently running the os on the cd
i am running ubuntu 10.04

---

### Post by TeoBigusGeekus on 2011-10-25
Open a terminal and give
```
gksu gparted
```
If it does nothing, install gparted
```
sudo apt-get install gparted
```
and try again.
Once inside, select your hd, right click it and select format (ntfs).

---

### Post by itsferny09 on 2011-10-25
got to gparted 
and it says:
partition:unallocated
file system:unallocated
does not let me format the hard drive

---

### Post by philinux on 2011-10-25
Can you take a screenshot of the gparted screen and post it.

---

### Post by itsferny09 on 2011-10-25
i firgured it out 
i created a new partition table
and then formated it to ntfs thank you for your help

---

