---
title: "Desktop Icons"
date: 2010-08-31
forum: General Help
---

### Post by jhapk on 2010-08-31
Hi,

in my home folder (/home/myusername) I had a whole bunch of folders. I deleted a default folder called "Desktop" and all the folders that are in my home folder now show on the Desktop as icons. Why is this? And how can I remove them from showing on the Desktop? 

Thanks

---

### Post by BrandyBear on 2010-08-31
Create a new Folder on the desktop Then Highlight all of the Icons (Left click and drag through all the icons) then keeping hold of the mouse button Hover the Coursor over the newly crated folder let go of the button then they should all be in that folder =):popcorn:

---

### Post by bergfly on 2010-08-31
The folder called Desktop is in fact a folder that contains whatever you choose to show up on the desktop. Deleting it seems to have confused the poor window manager. I would recreate the folder Desktop again.

---

### Post by BrandyBear on 2010-08-31
How would you recreate a desktop folder...?

---

### Post by bergfly on 2010-08-31
open places --> home and then in the window, right click and create folder. Call it Desktop

---

### Post by wojox on 2010-08-31
Open your Home Folder

Press Ctrl+H to show hidden files

Click on .config/user-dirs.dirs

Add 

*XDG_DESKTOP_DIR="$HOME/Desktop"*

Log out and back in.

:D

---

### Post by jhapk on 2010-08-31
Thanks Wojox,

that worked.

---

