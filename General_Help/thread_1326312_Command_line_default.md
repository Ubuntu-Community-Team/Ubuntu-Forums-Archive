---
title: "Command line default"
date: 2009-11-14
forum: General Help
---

### Post by robinzxp on 2009-11-14
Hi, I tried to install MX1000 mouse driver but it seems to have failed and I deleted the line I added to config file. However now when Ubuntu start it starts in command line mode, so I have to tytpe startx to start gui.

Any idea on how to make it normal again?

---

### Post by realzippy on 2009-11-14
Log in at the command line.Maybe there is a xorg.backup.Try:

[B]sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
[/B]

to restore configuration file.
If it is the same machine (other thread "desktop cube") where you (assuming) need ATI drivers you could try first:

**sudo apt-get install fglrx**

what would install ATI driver and create new configuration file
edit: *if* there are ATI drivers for x600;remember in 9.04 there was an issue,do not know;not running ATI ;-)
for some reasons...

---

### Post by robinzxp on 2009-11-14
Hi, thanks for reply. I fixed it by just reinstalling since it was really fresh install. Not sure how to close this topic, I'm newb

---

### Post by realzippy on 2009-11-14
> **robinzxp said:**
> Hi, thanks for reply. I fixed it by just reinstalling since it was really fresh install. Not sure how to close this topic, I'm newb

threadtools....above....in red letters ;-)

---

