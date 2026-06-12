---
title: "Stop users logging in through X"
date: 2010-08-27
forum: General Help
---

### Post by Monotoko on 2010-08-27
There is a user known as remote on my machine which I will only ever use for SSH, it has a limited set of admin commands (Reboot, update and a couple more)

Because it will only be used during an SSH session I would feel safer knowing that this user can only login through the command line and could not login through X or run startx to start the graphical manager going.

How would I go about this?

Daniel

---

### Post by x1a4 on 2010-08-28
Run gdmsetup: Alt+F2 then
```
gksudo gdmsetup
```
In the 'Users' tab you have the option to specify which users may/may not login through GDM.

---

### Post by airtonix on 2010-09-20
In lucid there is no Users tab.

---

### Post by 3Miro on 2010-09-20
Get Ubuntu alternate install and when you see the boot screen "Try/Install" then hit F4 and install Command Line only System.

---

