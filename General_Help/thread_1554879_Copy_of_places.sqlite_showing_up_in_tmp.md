---
title: "Copy of places.sqlite showing up in /tmp"
date: 2010-08-17
forum: General Help
---

### Post by cdawg92 on 2010-08-17
Just yesterday I noticed a file in /tmp, tmp<some hex sequence>.tmp
It was a rather large file and don't remember seeing before. I deleted the file only for it to show up again a short time later.
 
Looking at the file I found "SQLite format 3" in the header of the file so I opened it with SQLite Browser and found several tables that matched what is in places.sqlite under .mozilla, in fact the file sizes were a match. I have no idea what process is copying this file over, I rebooted and the file showed up just after logging in via GDM, so its definitely a process running under Gnome. Does anyone have any idea how this file is getting here? I'm concerned as the file has my complete browsing history and could be a security/privacy concern.

Thanks,
Carl.

---

