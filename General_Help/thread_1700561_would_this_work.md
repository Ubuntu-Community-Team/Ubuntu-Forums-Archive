---
title: "would this work?"
date: 2011-03-05
forum: General Help
---

### Post by wiggly81 on 2011-03-05
OK so im interested in trying some other distros, i love ubuntu and would not leave it but say for instance i wanted to install puppy as a dual boot system could i share my "/home" and "/swap" so all i would need to create in theory is a new "/" partition for the new distro?
would this cause problems, i cant personally see what big issues could be caused but i am new to Linux so i figure its always best to ask first.

---

### Post by vanadium on 2011-03-05
* Sharing the swap is not a problem
* Sharing the home directory is not a problem, provided you do not use the same user profile directory under different operating systems. This means in practice that you should use different user names on the different operating systems.

---

### Post by wiggly81 on 2011-03-05
thanx vanadium, i figured i would have to have a septate username to stop config files causing problem, just thought rather than having loads of partitions i can do it with 1 extra.

---

