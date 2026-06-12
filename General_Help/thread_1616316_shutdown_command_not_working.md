---
title: "shutdown command not working"
date: 2010-11-08
forum: General Help
---

### Post by me.translucent on 2010-11-08
I was very much used to using sudo shutdown time_in_mins .Untill it stopped workig.Now whenever i try to shutdown my computer using this command ubuntu tries to shutdown but after a few seconds a screen appears saying resume normal boot,root login etc etc ,can you guys help ? i can't figure out what has gone wrong.

---

### Post by I'mGeorge on 2010-11-08
what about sudo shutdown -h now ?

---

### Post by me.translucent on 2010-11-10
> **I'mGeorge said:**
> what about sudo shutdown -h now ?

yeah that worked , i am wondering why and why didn't the plain shutdown command work .Also the man page too wasn't of great help.what's the difference between 'bringing down a system' and 'halting' and 'turning it off'

---

### Post by efflandt on 2010-11-10
You are not really telling it what type of shutdown to do.  Maybe try **sudo shutdown -h +m** (where m is time_in_minutes).

**man shutdown**

Note that if you are doing it remotely (like through ssh) or closing the terminal you ran that from, you should end the commandline with **&** so it forks into the background and continues on after you log off.  Otherwise the shutdown command might be canceled as soon as you disconnect or are disconnected during shutdown:

**sudo shutdown -h +m &**

---

### Post by Ancanus on 2010-11-10
You can always create an alias to replicate the behaviour you had before.

They all pretty much do the same: terminate processes, sync drives, unmount drives... the difference is that at the end, some of them issue a reboot, some cut the power.

---

### Post by garvinrick4 on 2010-11-10
```
sudo halt
```shutdown
```
sudo shutdown -h now
```shutdown
```
sudo shutdown -r now
```restart
```
sudo reboot
```restart

---

### Post by me.translucent on 2010-11-11
i am wondering is there any thing for hibernate also ? (from terminal ofcourse)

---

