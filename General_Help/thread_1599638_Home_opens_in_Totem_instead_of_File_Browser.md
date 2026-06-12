---
title: "Home opens in Totem instead of File Browser?"
date: 2010-10-18
forum: General Help
---

### Post by garvinrick4 on 2010-10-18
I have one install that I have managed to get anything that I cannot right click and choose what I would like to open it in to open in Movie Player (totem) and for the life of me cannot remember where setting is. Did this before but cannot seem to remember how I fixed it. 
Anything under Places drop down menu you cannot right click on and select to open so opens in movie player.

---

### Post by yetiman64 on 2010-10-18
> **garvinrick4 said:**
> I have one install that I have managed to get anything that I cannot right click and choose what I would like to open it in to open in Movie Player (totem) and for the life of me cannot remember where setting is. Did this before but cannot seem to remember how I fixed it. 
Anything under Places drop down menu you cannot right click on and select to open so opens in movie player.

Check the files /usr/share/applications/defaults.list and /usr/share/applications/mimeinfo.cache and use the search funtion with the term "inode". Both the entries should read like,
> inode/directory=nautilus-folder-handler.desktop, I suspect one of them, most likely defaults.list has totem.desktop in it.

You may also need to check the filenames in ~/.local/share/applications if /usr/share/applications is OK.

edit: it is not defaults.list in ~/.local/share/applications but mimeapps.list and the other is still mimeinfo.cache

---

