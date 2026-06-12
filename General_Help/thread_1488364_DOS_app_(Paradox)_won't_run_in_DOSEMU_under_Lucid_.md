---
title: "DOS app (Paradox) won't run in DOSEMU under Lucid 10.04"
date: 2010-05-20
forum: General Help
---

### Post by berniev on 2010-05-20
Something changed?

Poor old Paradox was fine (actually it was great!) in DOSEMU 1.4.0.1 (Feb 11, 2010) under Karmic, but refuses to start under Lucid.
DOSEMU itself seems to be basically working ok.
Paradox does fire up ok in DOSBOX, but that is not an ideal place for anything except games (no print etc).

What might have changed? I'd really like to get this working again.

---

### Post by Kenneth D. Gladden on 2010-06-03
Several things have changed, sound does not work in dosemu under Lucid. 

Programs that ran fine under wine in 9.10 no longer work 
under Lucid

---

### Post by berniev on 2010-11-18
I'd still like to get this going again! ANYONE?

---

### Post by berniev on 2012-06-07
Yippee !

Now in Oneiric and tried again.  Installed from Ubuntu Software Centre.

In /etc/dosemu/dosemu.conf uncomment the line:  $_ignore_djgpp_null_derefs = (0)

and # echo 0 >/proc/sys/vm/mmap_min_addr

and my old friend works again.

---

