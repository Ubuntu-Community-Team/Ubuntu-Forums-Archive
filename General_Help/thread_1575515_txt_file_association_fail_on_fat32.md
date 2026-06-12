---
title: "txt file association fail on fat32"
date: 2010-09-15
forum: General Help
---

### Post by dewdrop_world on 2010-09-15
I have a Windows 7 partition, a fat32 partition that I use for moving data between Windows and Linux, and an Ubuntu partition.

On the Ubuntu partition, I can right click on a text file and the top of the menu says "open with 'gedit'." On the fat32 partition, the same action says just "open," and the "open with" submenu doesn't include gedit.

If I right-click and choose properties on the same file, the "open with" tab shows gedit as the default file association.

So that's weird... anyone else seen anything like this?
James

---

### Post by spjackson on 2010-09-16
When you right-click on a text file, the top of the menu says  "Open with 'gedit'" unless the file has execute permission set, in which case it shows "Open". When a FAT32 partition (or external USB) is mounted, all the files have the execute permission, so that is why you are seeing this effect on your FAT32 text files.

---

### Post by efflandt on 2010-09-16
Because all files on FAT32 appear to have the execute bit set (no concept of execute permissions), once you click **open**, it will then ask if you want to run the file or open with gedit.

It would likewise do the same for any actual executable script.  It just does not do that in one step for some reason.

---

