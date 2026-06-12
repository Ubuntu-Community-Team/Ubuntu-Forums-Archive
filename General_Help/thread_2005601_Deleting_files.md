---
title: "Deleting files"
date: 2012-06-17
forum: General Help
---

### Post by Shiryu on 2012-06-17
I am using KDE interface with Dolphin.

When I delete a file that is in another partition or in a pendrive, it moves the file to the trash can that is in the main partition.

It also happens when I delete a file from a folder that is mounted with sshfs, it downloads the file and insert it in the local trash can.

The trash can is enabled because I may need a deleted file again.
But I have no need to recover files that are not in the main partition.
Files from pendrive or sshfs folder should be directly deleted.

---

### Post by SeijiSensei on 2012-06-17
If you hold down Shift while pressing Delete, the file will be deleted rather than sent to Trash.  You can tell Dolphin to include the delete function in the context menu by navigating to Settings > Configure Dolphin > General > Context Menu and checking the box for "Show Delete Command".  Now if you right-click on a file, you'll have the option of moving the file to Trash or deleting it unconditionally.

---

