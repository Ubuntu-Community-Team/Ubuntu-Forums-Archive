---
title: "Goofy scroll mechanism in 12.04"
date: 2012-06-17
forum: General Help
---

### Post by peyre on 2012-06-17
I just reinstalled 12.04 from scratch, and I've found that some programs have replaced the traditional righthand scroll bar with this goofy little double arrow thing that appears when you hover over the righthand side just right (see screenshot).  It's very annoying, especially if I've had a few.  Anyone know how to disable this behavior?

---

### Post by stinkeye on 2012-06-18
Terminal...
```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```

Log out/in

---

### Post by vasa1 on 2012-06-18
Longer version here: [https://bugs.launchpad.net/ayatana-scrollbar/+bug/948126](https://bugs.launchpad.net/ayatana-scrollbar/+bug/948126) comment #4

---

### Post by peyre on 2012-06-18
> **stinkeye said:**
> Terminal...
```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```

Log out/in

Looks like that worked, thanks!

---

