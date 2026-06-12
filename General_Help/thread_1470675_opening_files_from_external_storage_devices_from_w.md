---
title: "opening files from external storage devices from within applications"
date: 2010-05-03
forum: General Help
---

### Post by tsqueezer on 2010-05-03
Newbie question: Running various applications, including Open Office, I need to open files from my external hard drive, from within said application itself. But the file menus for all my applications list only the files of my primary hard drive, and I can't look at other drives. Surely there must be some way to do this.

---

### Post by jocko on 2010-05-03
They don't just list your primary hard drive or partition, they list the entire file system (but your primary partition happens to be the root "/" of the file system tree).
External drives are mounted in /media/, so just browse there with the applications "file open" window.
In gnome, the file browser has a side panel with links to devices mounted in /media/, not sure if xubuntu's file browser have anything similar.

---

### Post by tsqueezer on 2010-05-03
Thanks. I've been using Linux only for 24 hours. I don't know what I missed when I tried this before. This works with Open Office Writer. It doesn't work with Google Desktop because this application will not index external drives, I just learned. I wish there were something for Linux that does what Google desktop does, only for an attached external hard drive.

---

