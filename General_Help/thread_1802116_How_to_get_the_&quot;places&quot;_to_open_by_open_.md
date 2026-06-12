---
title: "How to get the &quot;places&quot; to open by open folder?"
date: 2011-07-11
forum: General Help
---

### Post by ssreddy555 on 2011-07-11
By mistake, I have set the things in "Places" menu in Ubuntu 11.04 classic (Home, Documents etc) to open by Chromium browser. How can I restore it to original setting?.

Thank u.

---

### Post by ajgreeny on 2011-07-11
Use Alt+F2 command "nautilus" to open nautilus if you can not get it from the menu, right click on a folder and choose *Properties ->Open with* tab, and in that choose *File manager* or *nautilus*, or however it is listed.

---

### Post by ssreddy555 on 2011-07-11
As soon as I right click on any folder in the desktop "Places" menu (Home Folder, Desktop, Documents Etc.,), it is opening in the browser. The same with left click also.

Folders are opening normally within the Nautilus. Nautilus can be opened from "Computer" in the "Places" menu apart from the Terminal. I don't find "open with" option on right clicking any folder within the Nautilus.There is an "open" option but it opens the folder normally.

---

### Post by mc4man on 2011-07-12
Browse to your home folder > (view - show hidden files), > .local/share/applications
Go ahead and delete the mimeapps.list file inside
(it can be edited but just delete it
Things will return to normal

---

### Post by ssreddy555 on 2011-07-12
> **mc4man said:**
> Browse to your home folder > (view - show hidden files), > .local/share/applications
Go ahead and delete the mimeapps.list file inside
(it can be edited but just delete it
Things will return to normal

Yes, Sir; this worked. It was very annoying.

Thanks a lot.

---

