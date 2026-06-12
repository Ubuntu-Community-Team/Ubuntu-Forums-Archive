---
title: "hamachi connection issue"
date: 2011-07-28
forum: General Help
---

### Post by BlakeR721 on 2011-07-28
so recently I installed hamachi2 on my system, I fallowed all the steps I was give. but when I logged in I noticed on my other comp that it was showing exclamation point beside my name.upon further investigation it showed:

connection (!)direct[in red]
authentication legacy[in red]

Then when I restart hamachi the green circle beside my name stays flashing(connection) and does not fully connect

how do i solve this issue?

---

### Post by erikvanberkum on 2011-08-29
I had the same issue with version logmein-hamachi 2.0.1.15-1 but with the newer version on a new clean install logmein-hamachi 2.1.0.17-1 the issue is gone. 

The problem started after rebooting the machine that was running 2.0.1.15-1 before that it worked fine.

After installation i rebooted the machine had to:
sudo hamachi start
sudo hamachi login
sudo hamachi join yournetwork andpassword

After this my problems disappeared

---

