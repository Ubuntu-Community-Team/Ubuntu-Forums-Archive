---
title: "Screen freezes after laptop lid closed"
date: 2011-04-29
forum: General Help
---

### Post by rkrizan on 2011-04-29
If I close my laptop lid for more than a few seconds, my screen will become completely unresponsive, aside from the cursor. Any idea what could be causing this? :confused:

---

### Post by dino99 on 2011-04-29
think about either:
- graphic issue: system admin additional driver: activated ?
- suspend/hibernate problem: check swap

and of course: check errors logged into .xsession-errors and /var/log (system admin logviewer)

---

### Post by ppafin on 2011-05-01
I suffer this same issue. I found this;

[https://bugs.launchpad.net/ubuntu/natty/+source/compiz/+bug/740126](https://bugs.launchpad.net/ubuntu/natty/+source/compiz/+bug/740126)

---

### Post by tbresson on 2011-05-04
I have to same problem. Didn't before I upgraded.

---

### Post by Jorn Skorstad on 2011-05-19
I had the same problem. Deactivating Vsync in Compizconfig cured the problem for me.

---

