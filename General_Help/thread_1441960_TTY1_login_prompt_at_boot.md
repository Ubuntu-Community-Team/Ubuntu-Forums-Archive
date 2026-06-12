---
title: "TTY1 login prompt at boot"
date: 2010-03-29
forum: General Help
---

### Post by worm94 on 2010-03-29
A few weeks ago I installed Ubuntu Karmic (32 bit) after having been using Windows XP for a couple of months. Ever since I installed, when I start my computer I get a login prompt from TTY1. If said prompt is ignored, after a while it goes to GDM and I can login normally. I have tried entering my username and password when asked and all it does is show a command line. Again, if I wait after entering username and password, it goes to GDM and I can login normally. The weird thing is (for me at least :D) that if I enter my username and password and do startx in the command line, it goes to my desktop and everything works like it usually does, but after a while (about the same time it takes it to get to GDM if the TTY1 login prompt is ignored) it goes to GDM. After this, if I check with the "who" command in the terminal, it shows two sessions with my username.

I found a similar post ([http://ubuntuforums.org/showthread.php?t=1336921](http://ubuntuforums.org/showthread.php?t=1336921)) and the suggestion made there was to delete tty1  from /etc/init/, but I'm not comfortable with deleting important things. Anyone has any idea?

---

### Post by ademey on 2010-10-19
I posted a bug report half a year ago on exactly the same issue (see link below). On what machine did it occur to you? laptop/desktop, brand, model, graphics driver?

[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/498586](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/498586)

---

