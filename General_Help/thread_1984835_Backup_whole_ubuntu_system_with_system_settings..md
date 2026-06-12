---
title: "Backup whole ubuntu system with system settings."
date: 2012-05-22
forum: General Help
---

### Post by sorabh.v6 on 2012-05-22
I searched every where but didn't find any how to's for backing up whole system with system settings.My linux partition is 6GB only so can i back it up in my 8gb pen drive?

---

### Post by mörgæs on 2012-05-22
This is an option:
[http://ubuntuforums.org/showpost.php?p=9931677&postcount=4](http://ubuntuforums.org/showpost.php?p=9931677&postcount=4)

I have not tried it myself, though.

---

### Post by sudodus on 2012-05-22
One way to do it is to make an ***image file*** (compressed), that can be restored to an exact copy (clone) of your present hard drive or partition(s).

A tool to do that is Clonezilla. Make a boot CD or USB drive with Clonezilla, and boot your computer from that.

Another way is to copy your files with ***rsync*** or some graphical user interface tool using rsync to make a backup of your linux system. It is easier to backup and restore compared to Windows. You will probably get several suggestions, what tool to use within a few minutes...

---

