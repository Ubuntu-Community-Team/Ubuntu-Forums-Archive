---
title: "Common Home Directory Folders and Settings Dissapeared"
date: 2012-04-21
forum: General Help
---

### Post by dcajacob on 2012-04-21
Hi,

I am a longtime Ubuntu user with a new problem.  A few nights ago my session seemed to freeze.  I tried killing the offending app, but to no avail.  I left it like that overnight and the next afternoon, still in the same state, I hard-rebooted the laptop.

Reboot went fine, but when I logged back into my session, all my desktop customizations were gone, like a fresh install.  My home directory still has most of my files, but certain directories, like Download, Documents, Videos, etc. appear to be empty.

Running ls -llah from the terminal, I see that I actually have duplicates for those common directories!  See below (only showing duplicated stuff):

```
drwx------  17 dan  dan  4.0K 2012-04-19 20:12 .cache
drwx------  17 dan  dan  4.0K 2012-04-19 20:12 .cache
drwx------  16 dan  dan  4.0K 2012-04-20 22:24 .config
drwx------  16 dan  dan  4.0K 2012-04-20 22:24 .config
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Desktop
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Desktop
-rw-rw-r--   1 dan  dan    96 2012-04-19 20:10 .dmrc
-rw-rw-r--   1 dan  dan    96 2012-04-19 20:10 .dmrc
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Documents
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Documents
drwxr-xr-x   2 dan  dan  4.0K 2012-04-21 13:51 Downloads
drwxr-xr-x   2 dan  dan  4.0K 2012-04-21 13:51 Downloads
drwx------   4 dan  dan  4.0K 2012-04-19 20:10 .gconf
drwx------   4 dan  dan  4.0K 2012-04-19 20:10 .gconf
drwx------   5 dan  dan  4.0K 2012-04-19 19:53 .gnome2
drwx------   5 dan  dan  4.0K 2012-04-19 19:53 .gnome2
drwx------   2 dan  dan  4.0K 2012-04-19 19:53 .gnome2_private
drwx------   2 dan  dan  4.0K 2012-04-19 19:53 .gnome2_private
dr-x------   2 dan  dan     0 2012-04-19 20:10 .gvfs
dr-x------   2 dan  dan     0 2012-04-19 20:10 .gvfs
-rw-rw-r--   1 dan  dan   169 2012-04-19 20:34 .gtk-bookmarks
-rw-rw-r--   1 dan  dan   169 2012-04-19 20:34 .gtk-bookmarks
drwxr-xr-x   3 dan  dan  4.0K 2012-04-19 19:50 .local
drwxr-xr-x   3 dan  dan  4.0K 2012-04-19 19:50 .local
drwx------   3 dan  dan  4.0K 2012-04-19 19:50 .mission-control
drwx------   3 dan  dan  4.0K 2012-04-19 19:50 .mission-control
-rwxr-x
drwx------   4 dan  dan  4.0K 2012-04-19 20:12 .mozilla
drwx------   4 dan  dan  4.0K 2012-04-19 20:12 .mozilla
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Music
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Music
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Pictures
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Pictures
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Public
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Public
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Templates
drwxr-xr-x   2 dan  dan  4.0K 2012-04-19 19:50 Templates
```

The fact that my browsers and some other programs seem to think I am using them for the first time probably has to do with the duplication (and apparent emptiness) of the config directories.

I am hoping that the files that were in some of these directories are somehow recoverable.  Most of it is backed up, but not all of it.

Has anyone ever encountered a problem like this?

I don't recall what program hung, but it definitely wouldn't have been something that would do this.

I do use ecryptfs too, if that could have anything to do with it.  But most of my home directory decrypts fine.

---

### Post by paul_j on 2012-04-22
Hi,

Not sure if I can help, but have just experienced similar problem. 60% of my files and folders just vanished, had a similar freeze you mentioned last night but system appeared ok afterwards and have been running for several hours until files vanished

on mine if I use the find command to search for missing files, they show up ok, but ls or gedit can not find them at all. Desperately looking for a solution myself. 

Best Regards,
Paul

---

