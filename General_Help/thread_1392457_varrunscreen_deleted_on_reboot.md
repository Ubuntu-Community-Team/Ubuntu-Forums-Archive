---
title: "/var/run/screen deleted on reboot"
date: 2010-01-28
forum: General Help
---

### Post by tlgrok on 2010-01-28
I am using Karmic Koala. Whenever I reboot my computer, the folder /var/run/screen (used by [GNU screen]("http://packages.ubuntu.com/karmic/screen")) disappears [1]. To get screen to work, I need to do the following:[INDENT][FONT=Courier New]sudo mkdir /var/run/screen
sudo chown root:utmp /var/run/screen
sudo chmod 775 /var/run/screen
[/FONT][/INDENT]But this is only helps until the next reboot. Removing and reinstalling screen using apt-get did not help.

Anyone has any ideas?

[1] That is to say, it is deleted and not created again. /etc/init.d/screen-cleanup deletes and recreates it, and indeed manually running it (as root) is a temporary fix.

---

### Post by diesch on 2010-01-28
*/var/run/ *is on a tmpfs so it's not stored on disk but in memory and can't survive a reboot.

*/etc/init.d/screen-cleanup* should automatically run at start up. What does
```
ls /etc/rc?.d/*screen-cleanup
```
say?

---

### Post by tlgrok on 2010-01-28
[INDENT][FONT=Courier New]/etc/rcS.d/S70screen-cleanup[/FONT]
[/INDENT]This is simply a symlink to /etc/init.d/screen-cleanup .

---

### Post by tlgrok on 2010-02-11
Since posting the above, I have noticed that CUPS doesn't run on system start - that is, to be able to print something, I must[INDENT][FONT=Courier New] sudo /etc/init.d/cups start[/FONT]
[/INDENT]Together with [FONT=Courier New]screen-cleanup[/FONT]'s failure to run, this suggests that something's gone wrong with my boot process. Any ideas as to what it might be?

---

