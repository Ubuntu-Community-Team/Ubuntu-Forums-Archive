---
title: "symbolic link and dropbox"
date: 2012-08-14
forum: General Help
---

### Post by emagar on 2012-08-14
Hello Ubuntu Forums,

My office machine runs win7, my laptop runs ubuntu 12.04. Dropbox syncs my personal files in both. Files are organized in many folders and sub-folders.

In Linux, I created a symbolic link from one folder to another (both in the dropbox-synced part of my drive). I was expecting this to show as rubbish in my office machine (a broken link). That, at least, is what I remember happening a few years ago. 

To my surprise, the link is functional in the win7 machine. Does anyone know if symbolic links are now operational across systems? Or did Dropbox duplicate the directory in my office HDD?

---

### Post by MrsUser on 2012-09-28
From the application's point of view (how Dropbox 'sees' it), it's a folder and its contents that is being synced. If you create a symbolic link in Linux, then Dropbox 'thinks' this is a folder and syncs it to the cloud.

Then, when you're in Windows 7, the folder in the cloud will be synced to your Windows machine. Windows' Dropbox app cannot 'know' what happened on your Linux machine, if it's a folder or symbolic link. From the application's view, it's a folder with content which is in the cloud.

---

### Post by emagar on 2012-10-04
> **MrsUser said:**
> From the application's point of view (how Dropbox 'sees' it), it's a folder and its contents that is being synced. If you create a symbolic link in Linux, then Dropbox 'thinks' this is a folder and syncs it to the cloud.

Then, when you're in Windows 7, the folder in the cloud will be synced to your Windows machine. Windows' Dropbox app cannot 'know' what happened on your Linux machine, if it's a folder or symbolic link. From the application's view, it's a folder with content which is in the cloud.

Thanks to MrsUser, this actually solves the mystery. Thumbs up!

---

