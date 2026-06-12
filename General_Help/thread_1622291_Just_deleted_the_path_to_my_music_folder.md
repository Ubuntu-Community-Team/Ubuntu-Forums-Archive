---
title: "Just deleted the path to my music folder"
date: 2010-11-15
forum: General Help
---

### Post by cotsy on 2010-11-15
So..I was messing around with a couple of media players and somehow in the process, I've managed to delete the path to my music folder....so i cant find any my music anywhere....any suggestions on how to retrieve the files?

---

### Post by pqwoerituytrueiwoq on 2010-11-15
lets hope it is just in your trash can
your trash files
/home/chad/.local/share/Trash/files/
your root trash you must be root to view content
/root/.local/share/Trash/files/
command to view root trash
```
sudo ls /root/.local/share/Trash/files/
```
if it is not there your only option to get it back (without download/riping it/copying from backup) is a data recovery app

---

### Post by TiBaal89 on 2010-11-15
Eh oh... did you delete it while using the file browser or where you issuing commands in the terminal?  Hopefully you were in the file browser and they're just in the trash can!  Otherwise, that might not be pretty...

---

### Post by cotsy on 2010-11-15
Its not in my trash......getting kind of freaked now!!!and i deleted it in the player not the command line

---

### Post by ell02 on 2010-11-15
Try this,go to home folder with your file manager,then in the view tab select hidden.Look to see if there are any folders with the name of those music players.

---

### Post by ajgreeny on 2010-11-15
Which music players?  I seem to remember that if using kde applications, even on a gnome desktop, the things deleted using the application go to kde's trash, which I think is somewhere in the hidden ~/.kde folder in your home.  Alternatively, if you can remember the name of one of the missing files or folders you can run ```
sudo updatedb
locate <name of file>
``` or use the **find** command

---

