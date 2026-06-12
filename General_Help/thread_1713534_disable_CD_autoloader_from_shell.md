---
title: "disable CD autoloader from shell"
date: 2011-03-24
forum: General Help
---

### Post by buchs on 2011-03-24
I have an automated backup script that runs from cron. It ejects and loads a CD. I have been unable, thus far, to determine how to avoid interference from the desktop automounter. I've tried a variety of u/mounts and delays, but I still get a dialog on a desktop session saying: > Unable to mount CDROM.  Error mounting, mount exited with exit code 1: helper failed with: mount: /dev/sr0 already mounted or /media/cdrom0 busy. I am thinking that perhaps I could disable the automount temporarily from a shell command(s). Any suggestions in this regard would be appreciated.

---

### Post by blueridgedog on 2011-03-24
Take a look at this page:

[http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/](http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/)

---

### Post by buchs on 2011-03-24
Blueridgedog,

Thanks! Excellent bird, by the way.

---

