---
title: "no login promt on startup..."
date: 2010-09-28
forum: General Help
---

### Post by ealymbaev on 2010-09-28
Always was alright until I installed RVM and ruby 1.9.2.
After this I rebooted my PC and just got default wallpaper and NO LOGIN PROMT...

I tried CTRL+ALT+F1 and:

- startx ===> already running
- gdm ====> already running
-also tried dpkg-reconfigure xserver-xorg
- also tried apt-get install --reinstall gdm

NOTHING helps (( any other help?

P.S. tried reinstalling ubuntu twice - both times after installing ruby - same thing happens (
How can i fix this?

---

### Post by ealymbaev on 2010-09-29
bump. Help please

---

### Post by luvshines on 2010-09-29
You are not able to login to the machine ??

From terminal too ??
Have you tried 'single user' mode ?

---

### Post by ealymbaev on 2010-09-29
No, I am able to login through CTRL ALT F1 ==> tty1
From terminal it works. BUT when going to CTRL ALT F7 - there is no any login promt and bottom line. There is only default wallpaper of ubuntu and mouse pointer... thats all!

---

### Post by linux-hack on 2010-09-29
did you try ```
dpkg-reconfigure gnome-session
```

---

### Post by luvshines on 2010-09-29
This one reports the same problem:
[http://ubuntuforums.org/showthread.php?t=1568967](http://ubuntuforums.org/showthread.php?t=1568967)

This one suggests some things to be done:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1540427](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1540427)

---

### Post by ealymbaev on 2010-09-29
> **linux-hack said:**
> did you try ```
dpkg-reconfigure gnome-session
```

yes i tried it - the same result...
and tried 2 links above - the same...

How do you think - getting 10.10 will help me?

---

### Post by hrickh on 2010-09-29
> **ealymbaev said:**
> yes i tried it - the same result...
and tried 2 links above - the same...

How do you think - getting 10.10 will help me?
I've had the same thing happen to me, and I can tell you from personal experience that the second link, last comment was the culprit.

It was *always* a USB disk/stick that was being checked.

Make sure that you only have local disks plugged in while booting.

R.
==

---

### Post by ealymbaev on 2010-09-29
But I didn't even plug any other USB disks or sticks... )
It all went mad after installing RVM and ruby 1.9.2

---

### Post by luvshines on 2010-09-29
Can you try uninstalling the packages which screwed it all up ??

---

### Post by ealymbaev on 2010-09-29
I installed ruby using RVM - some kind of packet manager. Yes it has remove command. BUT i need this ruby 1.9.2 - so even if i remove it and system works again - it doesn't solve my problem )

By the way - there is some more information about my problem:
1. After loading to default wallpaper - if I push power button - the turn off dialog box appears and it works )
2. Sometimes before going to default wallpaper there is a text in terminal like "Glib_warning..", but it shows for just a second or 2

---

