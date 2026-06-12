---
title: "Make shortcut (link) for root folder"
date: 2011-11-06
forum: General Help
---

### Post by brunolabs on 2011-11-06
Hi.

How can I make a desktop shortcut (link) to a folder located in the root dir '/'? In the right-click menu the option is greyed out.


Thanks.

---

### Post by hwttdz on 2011-11-06
That's because you don't have permissions, you could either launch nautilus as root using 'gksu nautilus' or use the command line to make the link, 'sudo ln -s /path/to/target /path/to/link'

---

### Post by brunolabs on 2011-11-06
> **hwttdz said:**
> That's because you don't have permissions, you could either launch nautilus as root using 'gksu nautilus' or use the command line to make the link, 'sudo ln -s /path/to/target /path/to/link'

I tried that before but with 'link' instead of 'ln'.
It worked. Thanks.

---

### Post by hwttdz on 2011-11-06
Ahh, yes, many of the basic commands are hugely abbreviated
list -> ls
remove -> rm
make directory -> mkdir
remove directory -> rmdir
change directory -> cd

After you get used to it it's nice to not have to type all the letters.  But for those who don't use the command line often, maybe some aliases would help.  Anyways, glad you got it solved.  Can I ask why you needed a link in /, I generally try to avoid messing with anything outside of my home directory.

---

### Post by brunolabs on 2011-11-06
I used 'link' because in the 'man link' help page it seemed that was the right function for this.


> Can I ask why you needed a link in /, I generally try to avoid messing with anything outside of my home directory.
To make a desktop shortcut to my windows partition.

---

### Post by hwttdz on 2011-11-06
> To make a desktop shortcut to my windows partition. 

Wouldn't that be better accomplished by?

ln -s /path/to/windows/partition ~/Desktop/windows_partition

which doesn't require any special permissions.

---

