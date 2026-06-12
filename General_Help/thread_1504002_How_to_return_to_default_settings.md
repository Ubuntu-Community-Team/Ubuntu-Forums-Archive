---
title: "How to return to default settings"
date: 2010-06-07
forum: General Help
---

### Post by c0brabg on 2010-06-07
Hi I need the command for returning my ubuntu netbook remix (newest version) to default settings. The problem is that when I installed a theme, the next time I booted the OS the screen starts blinking and when I enter my admin password, no icons appear. My laptop is Dell 1525.

---

### Post by Mark Phelps on 2010-06-07
There is no such general purpose option -- like System Restore in that Other OS.

Best approach, if you're going to experiment with stuff, is to use something along the lines of Clonezilla or Remastersys to back off your current install to some media you can restore from later.

You can, in some cases, remove packages and "go back" to what you had earlier -- but even that is dangerous because you can accidentally remove LOTS of stuff and end up with a nonworking machine.

---

### Post by c0brabg on 2010-06-08
No see I am looking for a way to delete the configurator file (for skins), because I think that is my source of the problem. Pls I need command on terminal and when I tried making another user account by the way, it said that I wasn't root admin (I was logged on through terminal with my original account and wrote command useradd and adduser). I downloaded "root" and then nothing happens. How can I make my old account root through terminal and make a second account.

---

### Post by kerry_s on 2010-06-08
at the login screen select fail safe, that will put you in terminal in that terminal you can run gui programs, for instance the file manager "nautilus --no-desktop", press ctrl+h to see the hidden files/folders that have the settings. i believe the 1 you want is ".themes".
when your done, file-> close
type "exit" to get back to the log in screen

if all else fails, deleting ".gconf" will set you back to like the first day you installed.

---

### Post by c0brabg on 2010-06-08
> **kerry_s said:**
> at the login screen select fail safe, that will put you in terminal in that terminal you can run gui programs, for instance the file manager "nautilus --no-desktop", press ctrl+h to see the hidden files/folders that have the settings. i believe the 1 you want is ".themes".
when your done, file-> close
type "exit" to get back to the log in screen

if all else fails, deleting ".gconf" will set you back to like the first day you installed.
Deleting .gconf helped thanks a lot :popcorn: from here on I won't install any themes :mad:

---

