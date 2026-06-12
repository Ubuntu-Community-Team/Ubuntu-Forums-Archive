---
title: "Where is only a terminal window available"
date: 2010-08-31
forum: General Help
---

### Post by mahmoodn on 2010-08-31
I changed my desktop from ubuntu to kubuntu (after installation) using three commands:
```
sudo apt-get install kubuntu-desktop ***Select kdm as dm***
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```
Now when I restart my computer, I see kubuntu login page and login with my user and password. However after that I only see a terminal window!! no taskbar, no icon... even the terminal window can not be resized. I think it didn't install successfully.

What should I do?:confused:

---

### Post by ilovelinux33467 on 2010-08-31
have you tried:

```
rm -r ~/.kde4
```

then logging off and logging in again?

---

### Post by prshah on 2010-08-31
> **mahmoodn said:**
> ***Select kdm as dm***

Try to start/restart the KDE Desktop Manager (KDM) as follows: 

a) Use Ctrl_Alt_F2 to switch to a virtual terminal.
b) login, and give the command ```
sudo service kdm start
``` (use "restart" instead of "start" if you get a message about kdm already running). The screen should flash for a couple of seconds, and then the KDM loading screen should appear. If you are returned to the prompt instead, use Ctrl_Alt_F7 (or F8, F9, F10) to check if KDE has started up.

If it has, please post back or information on how to switch it permanently. (Quick Hint: Press f10 at login screen and choose KDE).

Alternately, post back with your results for further troubleshooting.

---

### Post by mahmoodn on 2010-09-01
> **ilovelinux33467 said:**
> have you tried:

```
rm -r ~/.kde4
```

then logging off and logging in again?

There was no such file in my home directory. So I did the following and it works now.

> **prshah said:**
> Try to start/restart the KDE Desktop Manager (KDM) as follows: 

a) Use Ctrl_Alt_F2 to switch to a virtual terminal.
b) login, and give the command ```
sudo service kdm start
``` (use "restart" instead of "start" if you get a message about kdm already running). The screen should flash for a couple of seconds, and then the KDM loading screen should appear. If you are returned to the prompt instead, use Ctrl_Alt_F7 (or F8, F9, F10) to check if KDE has started up.

If it has, please post back or information on how to switch it permanently. (Quick Hint: Press f10 at login screen and choose KDE).

Alternately, post back with your results for further troubleshooting.
Thanks for that. It is now working

---

