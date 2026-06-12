---
title: "When I click on certain buttons it grays out and hangs. Help!"
date: 2009-11-08
forum: General Help
---

### Post by RPG Master on 2009-11-08
I don't know if this has anything to do with GTK, GNOME, or some bad config in my home folder but MAN is it getting annoying!

So sometimes when I click on a button the app (happens randomly to all apps) will hang and gray out. Please tell me how to fix this or anyway to trouble shoot it... I am lost :(

Also, this didn't start until after upgrading to Karmic :(

---

### Post by doonit on 2009-11-15
The same thing is happening to me. Greys out when opening large file or doing a Save As or calling up any dialoge box that has further options. Will usually sort itself out after 10 minutes or so but who's got 10 minutes? I'm a raw beginner to Linux and haven't a clue where to start with this one. Gigabyte T1028M. I installed Karmic fresh, no upgrades. Come from XP. HELP!!

---

### Post by 3rdalbum on 2009-11-15
Try installing the "iotop" package. Run "top" and "iotop" in two terminals, and then trigger the action that will cause the window to grey out. See what's at the top of the lists running in the terminals.

Usually when a window greys out temporarily, it means that either the CPU or I/O are working so hard that the signals from the window take a long time to reach X.

---

