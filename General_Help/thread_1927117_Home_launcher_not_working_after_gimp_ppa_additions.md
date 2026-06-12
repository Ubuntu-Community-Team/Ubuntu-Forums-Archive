---
title: "Home launcher not working after gimp ppa additions"
date: 2012-02-17
forum: General Help
---

### Post by qwertyjjj on 2012-02-17
11.10 has some missing dependencies such that gimp won;t install.
The workaround was this documented on these forums:
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get install gimp

```

The launcher seems to be working properly except for the Home icon.
Even when I do gksudo nautilus, I cannot see any of my home folders Documents, etc.
However, they are there as shown by a terminal listing:
```

ls -l
total 1464
drwxr-xr-x  2 jack jack    4096 2012-02-17 13:38 Desktop
drwxr-xr-x  3 jack jack    4096 2012-02-16 09:11 Documents
drwxr-xr-x  2 jack jack    4096 2012-02-17 16:03 Downloads
drwx------ 13 jack jack    4096 2012-02-17 18:37 Dropbox
drwxrwxr-x  2 jack jack    4096 2012-02-17 10:44 dumps
-rw-r--r--  1 jack jack     179 2012-02-13 12:50 examples.desktop
-rw-rw-r--  1 jack jack 1418763 2012-02-15 21:54 Firefox_wallpaper.png
drwxr-xr-x  2 jack jack    4096 2012-02-13 13:23 Music
drwxr-xr-x  2 jack jack    4096 2012-02-13 13:23 Pictures
drwxr-xr-x  2 jack jack    4096 2012-02-13 13:23 Public
-rw-rw-r--  1 jack jack       8 2012-02-14 21:38 scaling_max_freq
drwxr-xr-x  2 jack jack    4096 2012-02-13 13:23 Templates
drwxr-xr-x  2 jack jack    4096 2012-02-13 13:23 Videos
drwx------  4 jack jack    4096 2012-02-14 22:04 VirtualBox VMs

```

Any ideas what could be wrong or how I can fix the launcher?

---

### Post by qwertyjjj on 2012-02-18
Also, when I hover the mouse over the left hand side of the screen, it has stopped showing the launcher. I need to minimise allw indows to see it.
Is there a way to reinstall the launcher?
FWIW, when I gksudo nautilus and try and go to the root foler then /home, it crashes.
Only way I can see my files is through the terminal.

```

:~$ nautilus
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.8
GLib (gthread-posix.c): Unexpected error from C library during 'Invalid argument': pthread_cond_timedwait.  Aborting.
Aborted

```

I thought this might be the issue: [http://forums.dropbox.com/topic.php?id=54208&replies=7](http://forums.dropbox.com/topic.php?id=54208&replies=7)
Says that GTK libraries were updated so how do I reinstall what was there before I did the upgrade -f ?

---

### Post by qwertyjjj on 2012-02-20
So, I got this fixed by disabling the dropbox.so file but has the upgrade -f messed everything up? How can I rollback?
Even in Thunerbird now, some buttons appear greyed out instead of black but they still work when pressed. Is this all just some test repo where libraries are going to be messe dup for good?

---

