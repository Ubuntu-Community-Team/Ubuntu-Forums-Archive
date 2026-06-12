---
title: "boot-up straight into terminal?"
date: 2006-03-07
forum: General Help
---

### Post by ed_agamemnon on 2006-03-07
so, can i boot my ubuntu straight into the terminal and load the gdm manually later?

---

### Post by claes on 2006-03-07
All you have to do is to tell init not start the gdm daemon. If I remember correctly this is the command:

sudo update-rc.d -f gdm remove

Then you can start gdm with:
sudo /etc/init.d/gdm start


To get init to run it again:
sudo update-rc.d gdm start 20 2 3 4 5 .

Claes

---

