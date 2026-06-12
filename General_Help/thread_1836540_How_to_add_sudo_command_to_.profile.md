---
title: "How to add sudo command to .profile?"
date: 2011-08-31
forum: General Help
---

### Post by zhigang1992 on 2011-08-31
Hi, Someone please tell me that how to add a sudo command to .profile so that it can be executed every time my PC boot.
for instance, that I wanna add a settingcommand that related to software called "isatapd", but the problem is that the setting which will be aboard when the PC is shutdown....

(Sorry if this a stupid question to ask:D)

---

### Post by ajgreeny on 2011-08-31
Add the command to **/etc/rc.local** without the sudo prefix, just above the "exit  0" line, and it will be executed at boot, but make sure you know what you are doing.

If this is a command related to the GUI desdktop, that way may execute it too early, so you can either do it in other ways, (which I'll have to leave to others to tell you about), or utilize the sleep option on the command to make it wait a particular time..

---

