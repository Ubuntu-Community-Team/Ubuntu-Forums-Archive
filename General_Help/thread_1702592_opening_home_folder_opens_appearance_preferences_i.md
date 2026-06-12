---
title: "opening home folder opens appearance preferences instead"
date: 2011-03-08
forum: General Help
---

### Post by Mo0 Linux Newb on 2011-03-08
[LEFT]when i try to navigate to my home folder, or any folder for that matter from the main menu bar, it brings up the appearance preferences menu. it started doing after i made a new background picture using GIMP.
after setting the img file as the desk top using the appearance prefrences, this started happening. if anyone could help me fix this that would be awesome.
[/LEFT]

---

### Post by jquis8411 on 2011-03-08
Try```
sudo nano -w ~/.local/share/applications/mimeapps.list
``` and edit this line "inode/directory" to read inode/directory=nautilus-folder-handler.desktop;
The default application to open folders changed.
You may need to open the file with gedit, I had the same problen a few weeks ago.

---

### Post by Vaphell on 2011-03-08
sounds a lot like the issue many people have with 10.10 - default app for folders changed to something else (though i admit i don't get how that would happen in your case). Either way try rightclicking any folder to get context menu (run nautilus in terminal if necessary to get the filebrowser ), choose 'open with...', select 'filebrowser' and make sure that the checkbox setting the selection as the default is ticked.

---

### Post by Mo0 Linux Newb on 2011-03-09
a friend fix this for me thanks anyways

---

