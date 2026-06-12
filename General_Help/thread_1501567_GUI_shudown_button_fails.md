---
title: "GUI shudown button fails"
date: 2010-06-04
forum: General Help
---

### Post by ajgreeny on 2010-06-04
Sometimes when I attempt to shutdown my computer using either the quit applet in the panel, or just the menu "shutdown" dialog, the dialog box appears with the options of shutdown, restart, suspend or hibernate, but no matter which I choose nothing happens.  It has got to the point where I have added  launchers to the desktop to run the command in terminal ```
sudo shutdown -r (or -h) now
```It is not a big problem for me to do that then simply type my password, but I wonder if this is a known bug in lucid.  If it is, I can't find it.

I have a sempron 2400+, 2GB ram, and this is where it gets interesting, an ati 9200SE graphics card, which does suffer a few problems with lucid as it did in karmic.  I wonder if this is a symptom of this card playing up more than I had realised.

Anyone got any ideas?

---

### Post by ajgreeny on 2010-06-05
OK, solved I think.

After several says of intermittent searching I came upon a report somewhere, not actually in launchpad bugs, but suggesting a conflict with OpenOffice quickstart which I always enable in the panel.

It seems to me from a test, that if you have used the quickstart icon to open an OOo doc or file of any sort it will stop the shutdown, reboot or logout from doing anything.  Disabling the quickstart icon appears to solve the impasse that otherwise occurs.

I am marking this solved for the moment but if I am being too hasty, I shall return to the problem again.

---

