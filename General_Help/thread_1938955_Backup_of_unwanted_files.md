---
title: "Backup of unwanted files"
date: 2012-03-10
forum: General Help
---

### Post by HughJarse on 2012-03-10
Any way to stop Backup from saving Firefox cache folders?

---

### Post by ajgreeny on 2012-03-10
Yes, but it will depend on how you do the backup, and what application you are using.

As an example, I use grsync, and I can make a simple text file and point the system to that in the "Advanced options" tab with command```
--exclude-from=/home/*user*/.grsync/excludecache.txt
``` where the contents of excludecache.txt are ```
.cache
.adobe/Flash_Player/AssetCache
.mozilla/firefox/qn4bdmr0.default/Cache
.thunderbird/rqxrmg4n.default/Cache
.cache/chromium
.thumbnails
```ie, just a list of the folders I don't want backed up.

---

### Post by lovinglinux on 2012-03-13
If you are using the default Backup application (Déjà Dup), then you can configure the folders to ignore in the Folders section. There is a panel to add folders do ignore.

---

