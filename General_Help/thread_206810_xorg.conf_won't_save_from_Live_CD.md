---
title: "xorg.conf won't save from Live CD"
date: 2006-06-30
forum: General Help
---

### Post by AlexBryan on 2006-06-30
Hi, booting from the Live CD without installing Ubuntu, I can't save changes to xorg.conf. I need to edit the file and add a line to make my monitor work properly before I can log in. I've done this before, but with this new install  everytime I restart the changes I made didn't save. What might this be?

---

### Post by halfvolle melk on 2006-06-30
Once you're done setting it up, "startx" doesn't work?

---

### Post by AlexBryan on 2006-06-30
After setting it up, running startx gives this error:

Server is already active for display 0.
If this server is no longer running, remove /tmp/.Xo-lock and start again.

If I edit xorg.conf from the live CD then restarting would surely remove any settings I changed because there is norewhere for them to be saved, which I get. But before I formatted this laptop I did just that, the monitor only works if I add: Option "MonitorLayout" "LVDS,Auto" to a certain part of the xorg.conf, and last time I edited it, restarted and it worked, so therefore must have been saved. Does the live CD have some kind of memory?

---

### Post by halfvolle melk on 2006-07-03
Sorry, I lost track of this one.
[QUOTE=AlexBryan]After setting it up, running startx gives this error:

Server is already active for display 0.
If this server is no longer running, remove /tmp/.Xo-lock and start again.[/quote]
Well in that case you might try
```
sudo /etc/init.d/gdm stop
```
That should stop the Xserver alltogether. Then put the required options in xorg.conf and see if "startx" does work,

> last time I edited it, restarted and it worked, so therefore must have been saved. Does the live CD have some kind of memory?
AFAIK a live session resides in RAM entirely so rebooting will flush it. Fortunately rebooting is not required for restarting X. It's only needed when you change something to the kernel or after adjusting partitions. In addition you may want to try the [alternate install cd](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso). It won't allow you to run a live session, but will enable you to write config changes to your hard drive.

---

