---
title: "Terminal will not open and recurring Gconf error"
date: 2010-04-15
forum: General Help
---

### Post by susanw on 2010-04-15
Hello, 

I'm at a bit of a loss here: Terminal will not open, panel bar has disappeared, wireless does not work, only Cairo dock is letting me get to anything (openoffice, games etc run fine just with very limited graphics.) GParted will not accept normal password to check swapdrive is working.


I'm really not sure what is going on with my computer...


I am triple booting different versions of linux and windows XP. These errors happened after, but not immediately after deleting contents of a separate partition and installing new OS (which works great incidentally) but I do not see why this would affect the Karmic partition. 

The error message I get (repeated many many times) is:

"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details —  1: Could not send message to GConf daemon: Message did not receive a reply (timeout by message bus))"


Unfortunately all googling for Gconf help seems irrelevent or way to complicated.

All ideas welcome, thanks in advance,

---

### Post by renkinjutsu on 2010-04-15
make sure gnome-settings-daemon is running.. if not, run it.

are you running the full gnome desktop or just a wm with xinit?

---

### Post by susanw on 2010-04-15
In direct response:

From inside system monitor there's a process called usr/lib/gnome-settings-daemon/gnome-settings-daemon so I presume I am running it? It says it's sleeping. I do not know how to find out how it is running any other way, not having a terminal is quite limiting.

And yes I am running full version of Ubuntu Karmic complete with full gnome desktop as standard.

---

### Post by susanw on 2010-04-15
Without a terminal I do not know how to put any system logs or other useful information on here??

---

### Post by renkinjutsu on 2010-04-15
You can get to a virtual terminal by pressing ctrl+alt+F1

there, you can maybe create a new user just to see if this problem is user specific. ```
sudo useradd newuser
sudo passwd newuser
```
then go back to GDM or whatever by pressing ctrl+alt+F7 and log in to the new user to see if the problem is still there.

---

### Post by susanw on 2010-04-15
The following error messages occur when trying to login to a newly created user:
- Could not update ICEauthority file /home/newuser/ICEauthority

- There is a problem with the configuration server. (usr/lib/libgconf2-sanity-check-2 exited with status 256)

- Nautilus could not create the following required folders: /home/.newuser/Desktop, /home/newuser/.nautilus Before running Nautilus, please create these folders or set permissions such that Nautilus can create them/

Then a pretty orange screen with no useability  except mouse movement appears. No panels or such like. But at least Ctrl-Atrl-Bkspace works!

---

### Post by susanw on 2010-04-15
Quoted from: [http://ubuntuforums.org/archive/index.php/t-1334951.html](http://ubuntuforums.org/archive/index.php/t-1334951.html) which had a similiar issue

"I subsequently discovered that the original user can be fixed by deleting these directories in /home/original-user
.dbus
.gconf
.gconfd
.gnome2
.gnome2_private                                 "

I found the above possible fix but deleting files, the purpose of which I don't understand, seems a bit stupid... Would be alright if they were only in one user's accounts if I could just create another user but the fact that I cannot, it seems, create another user makes it more dodgy to me.

Plus I cannot seem to view the drive with the these files in many other files can be seen in a limited graphics version of nautilus but when I try to open the home folder the application closes.

---

### Post by susanw on 2010-04-15
It is a single user issue! Just tried logging in as an old user I had made and forgotten about which works fantastically. 

This is good, means installing lucid on the other partition wasn't a catastrophic thing to do..

Getting there....:)

---

### Post by susanw on 2010-04-15
Spolved it! Actually didn't think I would and was just going to wait for lucid to come along since the beta version of it was appearing so stable.

Solved by deleting the following files (don't ask me how this fix works though!)

.dbus
.gconf
.gconfd
.gnome2
.gnome2_private 
from within a specific user's home folder.

Quoted from ([http://ubuntuforums.org/archive/index.php/t-1334951.html](http://ubuntuforums.org/archive/index.php/t-1334951.html))

---

