---
title: "How delete entry in Gnome 2 Places Menu?"
date: 2011-09-18
forum: General Help
---

### Post by bsalem on 2011-09-18
On Ubuntu 10.10 Gnome 2, how does one remove an entry from the Places menu? The Admin/Preferences/"Edit Main Menu" doesn't seem to know about the Places menu which seems to be symlinks to mount points and selected dirs on the filesystem. I can't find where the data for this menu is, so that I could edit a dir or config file.

Any hints? Which hidden dir can I munge. I assume that the stuff is on files I own.

---

### Post by anshulfy on 2011-09-18
Browse computer from Places menu. On the sidepan, you see places menu. On right click, you have an option to remove Directories like Documents, Music, Pictures etc. and also the bookmarks you created.

---

### Post by francisv@comcast.net on 2011-09-26
> **anshulfy said:**
> Browse computer from Places menu. On the sidepan, you see places menu. On right click, you have an option to remove Directories like Documents, Music, Pictures etc. and also the bookmarks you created.
I've got the same issue. Have entries under "Places" for network connections which no longer exist.
I can't find a "sidepan" when browsing the computer. Only the files and folders I normally see in Nautilus. There's  no link or icon that represents these outdated connections or Documents, Music ect.
Menu editor does not show them. I'll start searching from the terminal by -name and maybe find
something that points me to where they are .
Surprised this is not a "right click - delete" operation.

---

### Post by francisv@comcast.net on 2011-09-26
Go to Places-Home Folder. When Nautilus opens and you see the files/folders go to the 
top menu bar and select Bookmarks - Edit Bookmarks. Scroll down to the items you want
to take off the places menu, Delete.
I had no trouble removing Music, Videos , Documents from the Places menu.

---

