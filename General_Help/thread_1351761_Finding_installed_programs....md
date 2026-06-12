---
title: "Finding installed programs..."
date: 2009-12-10
forum: General Help
---

### Post by Gizenshya on 2009-12-10
I've installed a zillion programs for Ubuntu (9.04).  The problem is... I only see a portion of them in my program menu thingy.

So... where did they go?  Sometimes I try installing a cool program... only to find that I already have it installed.  But I don't know where it went to, or how to run it.  I would like to add them to menus, but I don't know how to go about it.

I saw [this recent post](http://ubuntuforums.org/showthread.php?t=1351668) that outlines making a menu shortcut for things once I find them (and that actually reminded about asking this :) ).

The problem is I just don't know my way around the file system in Ubuntu (or linux in general).  So where are the programs?  :)

Also... instead of running a program from just any folder, can I add it to whatever that common program folder is, and add a shortcut from there, or does it first have to be added to a registry of some sort to work? (if that makes any sense)

Also...

for programs that I've uninstalled, how do I get their shortcuts to go away?

---

### Post by jbrown96 on 2009-12-10
You should be able to just delete any shortcuts you've made.

Programs usually get installed to /usr/bin/ or /usr/sbin/. 

In a terminal, you can usually find where the programs are if you know the name of it. ```
whereis command
``` will show you the location of command. If you don't know the name of the command, then you start typing what you think is the name in a terminal and press tab twice; it will list all matching entries, then you can run the whereis command and create a shortcut from that info.

---

### Post by Gizenshya on 2009-12-12
is there a command or place that lists installed programs?

congrats on reaching a kilobean!

---

### Post by Physical Hook on 2009-12-12
```
 
dpkg --get-selections

```

---

### Post by 3rdalbum on 2009-12-12
Take a look at the video tutorial in my signature.

Usually these days if a program from the repositories doesn't appear in your menu, it's because it's either a command-line program or a daemon (that runs in the background). Or, of course, it could be a Gnome Panel applet or something similar.

---

