---
title: "Gparted not working...?"
date: 2010-05-12
forum: General Help
---

### Post by ferret man on 2010-05-12
Trying to resize and move a partition on a USB flash drive, and then create another partition. libgparted doesn't work? Here's my bug report.

---

### Post by ferret man on 2010-05-12
Bump.

---

### Post by efflandt on 2010-05-12
How much data do you have on that partition?  You cannot shrink a partition to less than the total size of data on it.  And it may be using more than you realize by looking at the total of files sizes because files do not necessarily end up on sector boundaries, so actual disk use is somewhat more than the sum of the files.

---

### Post by ryan858 on 2010-05-12
[quote="Bug Report"]File system doesn't have expected sizes for Windows to like it.  Cluster size is 32k (32k expected); number of clusters is 61849 (61849 expected); size of FATs is **256 sectors (242 expected)**.

**The file system is bigger than its volume!**[/quote]

Basically, it's trying to extend /dev/sdb1 past the actual last sector... Try reducing the size of that partition by 1MB (1024 kilobytes, 1048576 bytes) from the end. That should leave room for error in the *reported sector count* vs *actual sector count*... You will lose 1MB to free space (or less, depending on the amount of error in the sector count), but that's hardly anything at all, and shouldn't affect anything. If it does the same thing, try reducing it up to 10MB... If that doesn't get it, nothing will, and it's probably a different issue.

Reply back here if anything goes wrong (which it shouldn't).
Good Luck!

---

### Post by ferret man on 2010-05-13
Yes, well, it does the same thing for 1 MB and 10 MB... I posted the htm on the web, here. [http://dra1nerdrake.webs.com/gparted_details.htm](http://dra1nerdrake.webs.com/gparted_details.htm)

---

