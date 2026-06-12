---
title: "How do i downgrade this package..."
date: 2011-09-05
forum: General Help
---

### Post by brianrobles204 on 2011-09-05
Hi guys,

Been messing with my ubuntu too much, and now i have a problem :(
I've been trying to install libgtk2.0-*dev* to fix a dependency, but when i use apt-get, it says that I need libgtk2.0-*0 (= 2.24.4-0ubuntu2)*, and the one i have is an upgraded *2.24.4-0ubuntu3~natty1*.

Well, I tried using
```
sudo apt-get install libgtk2.0-0=2.24.4-0ubuntu2
```
but then it wanted to delete all my favorite apps and replace them with kde stuff -_-

I downloaded the right deb online, but USC wont let me downgrade. I tried removing the package first, but then it wanted to uninstall almost all my gui apps, including the terminal -_- ...

I even tried building gtk+ 2.24.4 from source. No dice; nothing seemed to change...

If it helps, i'm running gnome 3 illegally on ubuntu 11.04. Any ideas?

---

### Post by brianrobles204 on 2011-09-05
Bump

---

### Post by raja.genupula on 2011-09-05
i think synaptic gonna help you on this issue . open synaptic manager and then search for this pkg . then install it again .

---

### Post by brianrobles204 on 2011-09-06
> **raja.genupula said:**
> i think synaptic gonna help you on this issue . open synaptic manager and then search for this pkg . then install it again .

It didn't work :( Synaptic wouldn't let me mark for reinstall. Trying to remove the package wanted to remove everything again, and install kde for some reason.

---

