---
title: "everything is segfaulting"
date: 2009-08-19
forum: General Help
---

### Post by dpsleep on 2009-08-19
this is driving me nuts. i've checked the memory, ive checked the hard drives. reinstalled jaunty. everything boots fine, but then i open a program and anywhere from 1-250 seconds from opeing it it segfaults. firefox, terminal, metacity, gdm, everything. and they all do it at different times not all at once. and things like gdm seem to only seg once in a while.

im pretty sure this is hardware.... but it has been working fine for a long time. any ideas what could be causeing this to happen?

please help me. :)

thanks,
dpsleep

---

### Post by prshah on 2009-08-19
> **dpsleep said:**
> 
im pretty sure this is hardware.... but it has been working fine for a long time. any ideas what could be causeing this to happen?


You had better run memtest on your memory, for atleast 2-6 hours (depending on your memory). Anything in RED is bad.

Failing that, maybe the fans are not working anymore? You'll need to open up the tower and check this, usually.

---

### Post by Barafu Albino Cheetah on 2009-08-19
95% it is a hardware problem. 
5% it is a damaged kernel

---

### Post by dpsleep on 2009-08-19
> **prshah said:**
> You had better run memtest on your memory, for atleast 2-6 hours (depending on your memory). Anything in RED is bad.

Failing that, maybe the fans are not working anymore? You'll need to open up the tower and check this, usually.

ok figured it out... it was memory. i did a memtest for 2 passes, but i guess that wasn't enough. thanks for helping, ubuntu is working great now.

---

