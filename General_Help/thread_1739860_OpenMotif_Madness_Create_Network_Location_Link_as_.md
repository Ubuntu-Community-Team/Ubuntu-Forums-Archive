---
title: "OpenMotif Madness: Create Network Location Link as Local Filesystem Location"
date: 2011-04-26
forum: General Help
---

### Post by UltraZone on 2011-04-26
I'm working with a program that uses Open Motif to create all of the widgets, including the Open File dialog box (obviously).  However, Open Motif being kinda old-timey, 80's vintage, and for the most part now an abandoned project, it is quite clunky.  So, actually what I need to do is to open some files located on my work server.  I have already successfully connected to the relevant server directories with Samba, and with programs built with GTK+ (such as  GIMP) I can open files across the network because I have created a bookmark in Nautilus, and those bookmarks appear in the Open File dialog box created by GTK+.  Now, Open Motif is different: it doesn't see network locations, orNautilus shortcuts.  When I type "smb://serveripyadayada" in the search folder, it really doesn't like it and complains.  So, what do I do?  Can I get somehow Open Motif to open a network location?  Or can I do a run-around and place a shortcut in the file system that points to the network location?  Halp!!

---

### Post by UltraZone on 2011-04-26
bump.

Comon guys.

---

### Post by Ibidem on 2011-07-28
"Better late than never"
You would have to mount the relevant location. gvfs-fuse is the most likely candidate, but I haven't played around with it at all.

---

