---
title: "Real-time synchronisation and backup application?"
date: 2011-12-17
forum: General Help
---

### Post by woodyg on 2011-12-17
I need an application that will synchronise and mirror my data on my main computer onto another backup computer (connected wirelessly with Samba) in real-time, i.e. whenever changes are made to my main computer - then these changes are implemented on the mirror/backup-computer. I have in the past been using LuckyBackup for backups, but I don't think it does real-time synchronisation. 

Suggestions? (only with GUI please)

---

### Post by searchfgold6789 on 2011-12-17
Look up "gtkrsync"

---

### Post by Lars Noodén on 2011-12-17
rsync is the obvious choice for synchronization.  To get invoked when files get changed you could try using inotify and [incron](http://packages.ubuntu.com/oneiric/incron).

---

### Post by woodyg on 2011-12-18
> **searchfgold6789 said:**
> Look up "gtkrsync"

Does gtkrsync make use of inotify or fsnotify?I haven't found much info on gtkrsync...

---

### Post by woodyg on 2011-12-18
> **Lars Noodén said:**
> rsync is the obvious choice for synchronization.  To get invoked when files get changed you could try using inotify and [incron]("http://packages.ubuntu.com/oneiric/incron").

If I don't fancy some diy, is there an application with a GUI that combine rsync (or equivalent) with inotify or fsnotify?

---

### Post by Lars Noodén on 2011-12-18
I only know the diy way.  It is likely to be much simpler and more flexible to DIY than to work through the configuration and customization of some pre-packaged solution.

---

### Post by Lars Noodén on 2011-12-18
I've been looking at inotify and there is a shortcoming in that it cannot (yet) check recursively in directories.  So it's not possible to point it at the top of a hierarchy and have it triggered by a change somewhere down in a subdirectory.  I expect that capability will eventually be added but right now it does not exist.

---

