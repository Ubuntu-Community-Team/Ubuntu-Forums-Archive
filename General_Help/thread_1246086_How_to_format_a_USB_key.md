---
title: "How to format a USB key?"
date: 2009-08-21
forum: General Help
---

### Post by JohneG on 2009-08-21
I have a USB key (4GB) that is showing up only 1GB. I used it to install UNR to my netbook and when i deleted the contents i realized its only showing up as 1GB. How can i format this?

---

### Post by fooman on 2009-08-21
go to system > administration > partition editor

when it opens,  look in the toolbar,  all the way to the right...you will see a drop down arrow.  click it and find the flash drive in the list.  click once on it and it should appear in the bottom section of the editor.  right-click on that and choose "unmount".  once it has been unmounted,  right-click it again and choose "format"...choose the file system,  then click apply in the toolbar.

** be careful using the partition editor....don't want to format the wrong drive/partition!! **

hope that helps.

---

### Post by ajgreeny on 2009-08-21
When you deleted the files from the flash drive they probably did not disappear, but went into the drives own trash folder.  You may be able to retrieve the space without formatting.  Just attach the drive and wait for nautilus to appear, then hit Ctrl+H to show hidden files and folders.  A .Trash-1000 or something similar may well appear containing all the deleted files etc.  You should be able to delete them from there, though I can't remember if it needs root privileges.  If it does just fire up nautilus as root with ```
gksudo nautilus
``` and delete them that way.

---

