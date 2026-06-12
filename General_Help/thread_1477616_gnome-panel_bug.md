---
title: "gnome-panel bug"
date: 2010-05-08
forum: General Help
---

### Post by cj.surrusco on 2010-05-08
I was messing around with the gnome panels today and I happened to place a panel directly below another panel on the top of my screen. I accidentally chose to auto-hide the lower panel. From that point on, absolutely everything in gnome has become unresponsive. Even on reboot, it still remains unresponsive.

Is there anything I can do to disable the gnome panel at startup and change the gconf setting for the panel's auto-hide? I've already tried using the recovery console to purge gnome-panel and reinstall it, but to no avail.

Any suggestions would be greatly appreciated.

---

### Post by cj.surrusco on 2010-05-08
removing gnome-panel altogether won't work either. right after logging in it brings me right back to the login screen.

---

### Post by unmole on 2010-05-08
how about a
```
sudo debconf gnome-panel
``` to reset it back to default?

---

### Post by cj.surrusco on 2010-05-09
That won't work either since debconf can't be opened in recovery mode. I've tried the gconf command line version, gconftool-2, but I can't get that to work for me.

---

### Post by mo79 on 2010-05-09
Try this: [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

---

### Post by cj.surrusco on 2010-05-09
> **mo79 said:**
> Try this: [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

Thanks for the response, but gnome is completely unresponsive, there is no way to run that kind of program. I need a fix that can work from recovery mode.

---

### Post by cj.surrusco on 2010-05-09
I was able to solve the problem by reseting the gnome panel to default by removing the panel directory from gconf.

---

### Post by mojo risin on 2010-07-19
> **mo79 said:**
> Try this: [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)
Thank you, it solved my problem (hid the top bar below the bottom bar in hope to get more space. was a mistake obviously since it had the problem as anybody else had who tried it :d'oh:

---

