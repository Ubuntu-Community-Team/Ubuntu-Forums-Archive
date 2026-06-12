---
title: "Panels got shuffled"
date: 2009-10-26
forum: General Help
---

### Post by G1imt on 2009-10-26
For some reason (after a restart, i think) the items on the panels have been shuffled. Actually it looks like the items have been mirrored, since, for instance, the "Minimize all" button has been moved to the right of the bottom panel, and the status bar has been moved left in the top panel.

I managed to move the items back to some extent by unlocking and moving them, but the items again got further shuffled after a restart. If there a way i can simply "reset" the panels to their default appearance?

---

### Post by jhb1608 on 2009-10-26
> **G1imt said:**
> For some reason (after a restart, i think) the items on the panels have been shuffled. Actually it looks like the items have been mirrored, since, for instance, the "Minimize all" button has been moved to the right of the bottom panel, and the status bar has been moved left in the top panel.

I managed to move the items back to some extent by unlocking and moving them, but the items again got further shuffled after a restart. If there a way i can simply "reset" the panels to their default appearance?

I have that same problem until I fixed the issues by right click on every panel and go to "lock the pancel" then it will lock and won't go anywhere.

---

### Post by G1imt on 2009-10-26
I mean that it seems like my panels have been horizontally mirrored. I'm unable to pull the date/time and login items back to their original position, hence i need some kind of reset to default button.

Anyone?

---

### Post by GiveLove on 2010-01-13
Hello G1imt, :)

Check out this thread for an answer.
[http://ubuntuforums.org/showthread.php?t=1295804](http://ubuntuforums.org/showthread.php?t=1295804)

I have the same problem in 9.04.

GiveLove

---

### Post by Andreas1 on 2010-01-13
reset panel by (type in terminal):

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

beware: this will reset your panel to it's original default state.

---

