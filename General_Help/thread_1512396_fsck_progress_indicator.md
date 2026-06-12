---
title: "fsck progress indicator"
date: 2010-06-18
forum: General Help
---

### Post by Ronin_301 on 2010-06-18
So, I recently installed XUbuntu 10.04 on both my laptop and my desktop, and everything has been working fine except for one small irritation.

When fsck does its partition check every x number of mounts, it displays the current drive being checked and a progress bar on the Plymouth splash screen.

However, if I boot without the splash screen, it simply says "fsck from util-linux-ng 2.17.2" with no indicator showing how far along it is. It's not really a big deal, except I'd like to be able to have some visual feedback so I know my system hasn't frozen or anything. It used to work fine on 9.10, but hasn't since doing a fresh install of 10.04.

Any idea on how to achieve this behaviour?

---

### Post by dino99 on 2010-06-18
this is the normal design used, even if previous was better and more intuitive

---

### Post by nitrofurano on 2010-07-10
correction: this is misdesign, not design!
anyway, do someone know how can we get that fsck progress bar in text mode back? is it based in some configuration file like at '/etc/fsck/' or anywhere else?

---

### Post by Vimmander on 2010-08-01
Whoops...posted in the wrong topic and couldn't delete my post.  Sorry.

---

### Post by zeugmatis on 2010-10-28
This is absolutely terrible from a server perspective.  We want to know that the fsck is doing something, especially when we're under horrendous pressure to get a system back up.  Without any sort of feedback we're left with no communication from the machine as to if it is coming back up, and how much longer it will take.  

Any reason why this behavior was silently removed?

---

