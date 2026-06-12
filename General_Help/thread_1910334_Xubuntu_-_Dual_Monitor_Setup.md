---
title: "Xubuntu - Dual Monitor Setup"
date: 2012-01-16
forum: General Help
---

### Post by jordanpatrick on 2012-01-16
Hello all,

I have been tinkering with my Xubuntu install for a bit now trying to get my second monitor to act as an extended desktop, rather than a cloned desktop.

I have written a small script that uses xrandr to adjust the displays, and it works if I manually execute it after logging into Xubuntu, but I cannot seem to get it to run at login.

I tried putting the script in the Application Autostart folder, but it does not run at boot. I also tried placing it in /etc/X11/Xsession.d to no avail. My only guess is a permission issue perhaps? I am new to linux in general...I have the file set to be executable, the owner is root, my user account can R&W, others can read...

Script:
```
    [LEFT]#!/bin/sh[/LEFT]
xrandr --auto --output DVI-0 --mode 1280x1024 --right-of VGA-0

```

---

### Post by jordanpatrick on 2012-01-17
I chmod 755 the file to ensure that all users, processes, whatever should be able to use it, I believe. The script does work, just not automatically at login. Is there another way to do this? I read I can make changes to do this to Xorg.conf? But I am not sure where that file is, or how I am supposed to edit it in this case. Any suggestions?

---

