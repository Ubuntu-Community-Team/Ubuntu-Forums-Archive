---
title: "deleted downloads folder"
date: 2012-08-06
forum: General Help
---

### Post by Unguidedone on 2012-08-06
Its a simple problem but i deleted downloads folder.  I looked around in the recycle bin and its long gone. 

here is an older post about the same topic but no help

[http://ubuntuforums.org/showthread.php?t=1628123](http://ubuntuforums.org/showthread.php?t=1628123)

---

### Post by mcduck on 2012-08-06
Just create a new one, and then edit the ~/.config/user-dirs.dirs -file and make sure it contains the following line:
```
XDG_DOWNLOAD_DIR="$HOME/Downloads
```
(of course use the name you decided to use for your new downloads directory).

After that log out and back again, and the directory should be recognized again. Then just configure your web browser and any other program you want to save their downlaods there. They should all either have a settting in their options, or use the directory automatically.

---

