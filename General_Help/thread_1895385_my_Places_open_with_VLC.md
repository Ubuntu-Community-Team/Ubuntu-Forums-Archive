---
title: "my Places open with VLC"
date: 2011-12-14
forum: General Help
---

### Post by manchildjr on 2011-12-14
when i click places, then home or any other button it opens in VLC and not in file manager. Is there a way i can fix it? (btw i'm in ubuntu 10.10)

---

### Post by Krytarik on 2011-12-14
It seems like you inadvertently changed the default application to handle folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it and how to prevent that in future:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Notice that the concerning option, and possible cause of your issue, isn't included in the "Open With -> Other Application" dialog anymore, at least in Nautilus.

Regards.

---

