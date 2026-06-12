---
title: "Formated drive wont detect in windows"
date: 2010-04-26
forum: General Help
---

### Post by Bluestars on 2010-04-26
I used Gparted and formated an external hd to ext3 then back to ntfs and gave it a label.  Now when I plug it into a vista machine it doesnt show up under My Computer, though it does show up in Disk Management.  

How can I use Gparted to get the drive usable under Vista as well as Ubuntu?

---

### Post by efflandt on 2010-04-26
Did you remove the partition and recreate it or only reformat an existing partition.  It may be best to remove the partition and then partition and format it as ntfs from Windows.  Then Windows should recognize it and it will still be accessible to Linux.

---

