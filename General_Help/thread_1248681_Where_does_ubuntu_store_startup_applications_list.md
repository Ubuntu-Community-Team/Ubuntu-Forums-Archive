---
title: "Where does ubuntu store startup applications list?"
date: 2009-08-24
forum: General Help
---

### Post by abrari on 2009-08-24
Yes, in which file/folder does ubuntu store the list of applications that automatically started on startup? In case the system locked up on startup because of some bad startup apps, I can edit that list from root shell prompt to fix it.

Well, I have faced such problem, and all i can do is uninstalling the apps that i think it locked the system up. But I want to just edit list of startup apps, not remove them.

---

### Post by drs305 on 2009-08-24
Your user-assigned startup list is in ~/.config/autostart
You can just delete them from this folder or remove them via System, Preferences, Startup Applications/Sessions.

System startup apps are assigned to various /etc/rc.X folders  (0-6), and the /etc/rc.local file, with the main app referenced in /etc/init.d
There are specific procedures to remove these startup apps. Normally you remove the links from the rcX folders, not from the /etc/init.d folder itself.

```
update-rc.d -f *scriptname* remove	# removes links in rcX.d folders, not file in /etc/init.d
```
Refer to "man update-rc.d" for the details.

---

### Post by abrari on 2009-08-24
Thanks for your reply.

However, i just need the list of startup items assigned by me (since startup problems are usually occured after i manually add those apps to my startup preferences).

Those in /etc/rcX.d looks like essential system services. I won't touch that :D

---

