---
title: "some problems on my mouse"
date: 2011-02-02
forum: General Help
---

### Post by smandyscom on 2011-02-02
hi all

i dont know what's going on my mouse since last booting up, i believed my laptop not updated or get any system configuration changing.
but it happened several problems on my mouse, listed below:

1. left-hang configuration can't work. no matter i select right or left-hand configuration, it always works as right one.

2. my mouse was "locked" on the last dialog i clicked.
    for example, assuming i now opened 2 window, A and B. i browse A window at first with normally mouse working, suddenly i can't change windows on every places by mouse clicking.  my mouse pointer can be moved, but it just remained arrow, and nothing happens after clicking.
this only way to release is going to A window, and do a right-click. then it becomes normal.

i tried to re-modprobe usbhid, reinstall gnome-setting-daemon, but doesnt work.
and i dont install mouseemu and mousetweaks on this laptop.
and i use ubuntu 10.04.

now i totally have no idea to face this. if there's any thing i didn't describe clearly, please mention it, and i will try to make description better.

thanks!

---

### Post by smandyscom on 2011-02-02
i got a solution from 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571534](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571534)
by [jollywollup]("https://launchpad.net/%7Ejollywollup").

```
sudo service gdm restart
```
re-login could help this for awhile. it will turn bad randomly..
so i still want to solve this permanently.
ahh.. a little bit annoyed

---

