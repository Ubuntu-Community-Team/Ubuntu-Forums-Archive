---
title: "Simple backup /gzip loads cpu"
date: 2009-07-10
forum: General Help
---

### Post by brilyant on 2009-07-10
I have recently found an instance of gzip running which was slowing the entire system (Heron 8.04.3/Dual 3.4 GHz CPU).  I think this process was triggered off by Simple Backup.

Is there a way to discover the nice setting under which the process is running? My reading of a little bit of documentation says that SB is supposed to be as nice as possible.

Ta.

Andrew.

---

### Post by andrewc6l on 2009-07-10
From a console:
ps -eo pid,nice,user,comm,args

(And I just noticed that top shows the nice level NI as well by default.)

---

