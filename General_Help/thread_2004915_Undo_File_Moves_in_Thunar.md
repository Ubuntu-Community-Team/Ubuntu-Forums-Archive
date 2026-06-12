---
title: "Undo File Moves in Thunar"
date: 2012-06-16
forum: General Help
---

### Post by SillySod on 2012-06-16
Is it possible to undo a file copy or move operation in Thunar?

Sometimes I accidentally copy or move files, usually because I have or haven't pressed CTRL or SHIFT to copy or not copy as required.  After the operation completes, CTRL-Z doesn't do anything and there is no "Undo" option in the Edit menu.

---

### Post by mike555 on 2012-06-16
You might want to set up a custom action in thunar , the command to move a file somewhere is " mv %F $(zenity --file-selection --directory)  " without the quote marks .set it for all files but not directories .....

   the copy to command would be " cp %F $(zenity --file-selection --directory)" without the quote marks.....

 then you could just right click on a file and pick move or copy to...

---

