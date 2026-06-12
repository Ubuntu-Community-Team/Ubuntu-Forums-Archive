---
title: "Kubuntu 9.10 stalls at boot (shows mouse icon, keyboard inactive)"
date: 2009-12-26
forum: General Help
---

### Post by MysterySword on 2009-12-26
I was messing with the desktop effects when my computer froze (completely). I did a hard power off, and since then, its refused to boot. It's set to auto-login, and during bootup, the mouse shows on a black screen (and I can move it), but the keyboard is inactive (Num Lock and Caps Lock lights won't go on). It just stays at a black screen with the mouse icon forever.

I went to the Live CD and entered "e2fsck -f /dev/sda1", but that didn't solve the problem.

Help would be appreciated.

---

### Post by MysterySword on 2009-12-26
Solved. I deleted the .kde folder from the home directory on the live CD.

---

