---
title: "How can I uninstall a software installed with wine and has no uninstall.exe ?"
date: 2006-05-16
forum: General Help
---

### Post by Isoss on 2006-05-16
I have like 3 useless sotwares which I installed with wine and didn't work. I need to uninstall them but they don't seem to have an uninstaller file! what can I do? I hate keeping useless files in my system! hope someone knows. and thanks in advance.

---

### Post by xXx 0wn3d xXx on 2006-05-16
[QUOTE=Isoss]I have like 3 useless sotwares which I installed with wine and didn't work. I need to uninstall them but they don't seem to have an uninstaller file! what can I do? I hate keeping useless files in my system! hope someone knows. and thanks in advance.[/QUOTE]
Open nautilus file browser and then go under /home/username/.wine (make sure you have "Show hidden files checked. It's under view) from there go under "drive _c" and then "Program Files" you can delete the application folder. (ex: uTorrent)

---

### Post by user1397 on 2006-05-16
can't you just go to the /home/username/.wine/drive_c/Program Files directory to where you app's folder is, and delete it.  (it might also be just in /drive_c, because sometimes apps get installed there and not in Program Files.
btw, you have to enable hidden files in nautilus to view the ./wine folder

EDIT: MasterChief1234: you're better than me! :) 
(not surprising since you destroyed an entire covenant armada)

---

### Post by YokoZar on 2006-05-17
Better way:

open a terminal window and type "uninstaller"

This opens a Wine program analogous to the Windows "add/remove programs" function.

---

### Post by Isoss on 2006-05-18
I thought about deleting them. but thought there might be some kinda registery files like windows. so thought that might not work! but looks that even installing EXEs uder linux is different. So I guess that's what I've been looking for: Wine application uninstaller. Thanks guys and thank you YokoZar.

---

