---
title: "Could not get lock /var/lib/dpkg/lock"
date: 2011-04-01
forum: General Help
---

### Post by Katu Mala on 2011-04-01
What could be the problem (below) and how can I resolve it? This occurred after I do "sudo apt-get update" or before "sudo apt-get upgrade".

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? :(

Attached are two screen-capture of the errors, thus not allowing me to do update neither upgrade 
my system.

Thank you, to anyone who will help.

Katu
........:confused::confused:

---

### Post by u-noob-tu on 2011-04-01
that happens when you are installing programs by using two different installation methods (like using synaptic and software center at the same time). close one and do them one at a time. if it still gives the error, try a restart. 

hope this helps

---

### Post by Katu Mala on 2011-10-12
Thank you for help.

---

