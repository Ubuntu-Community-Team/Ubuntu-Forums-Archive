---
title: "Wine Problem"
date: 2011-03-18
forum: General Help
---

### Post by Trexss on 2011-03-18
Hello, i'v installed wine and i'v tried to run Wow.
The game is not in the same drive as ubuntu.
When i try to open the wow.exe witch wine it says: The file '/media/New Volume/Games/WoW/Wow.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.  How i can bypass this? iv tried properties/ premissions to allow executing file as program, but when i try that it will unnmark emmedietly. 
Pls help
The same happends witch other exe files
Sorry for my english :)
Thanks

---

### Post by galacticaboy on 2011-03-18
Right click on the file that you want to open with Wine, then click Permissions at the top, then make sure "Mark as Executable" is clicked, then reopen it with wine, should work now.

---

### Post by Trexss on 2011-03-18
I'v tried that, when i try to mark as executable it automatically unnmark

---

### Post by FlashHater on 2011-03-18
I've had the same problem trying to run an executable from an external drive. Try moving Wow.exe to the drive Ubuntu's on and then follow galacticaboy's instructions again.

---

### Post by galacticaboy on 2011-03-18
Open up a terminal, change to the directory that your game is in
cd ./"name of directory"

then type in 
chmod +x "name of file/game"
then hit enter, not try to open it, this is command line way of making it executable

---

