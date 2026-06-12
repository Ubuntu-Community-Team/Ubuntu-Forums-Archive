---
title: "Ubuntu keeps freazing on me"
date: 2010-04-07
forum: General Help
---

### Post by Illua on 2010-04-07
Hi,
im new to linux and all.
I got an asus laptop dual booted with ubuntu and vista (uhh) since im starting univercity and i have a programming class which we need linux for.
The problem is, every now and then (sometimes very often like today) ubuntu just freezes, completly and does not respond to absolutly anything, everything just stops, including the system monitor graphs, wanda the fish, the mouse.
Only way to get it to work is to turn it off the bad way.
Ill list my hardware if it wil help
Its an asus x59sr
intel core 2 duo
ati radeon hd3470
4gb dddr2 ram
Would really like some hepl since this keeps happening while im trying to code and lose all the code i didnt save
Thanks a bunch

---

### Post by hugo007 on 2010-04-07
try disable all hibernate options and put it on fullpower.It should be a energy issue like trying to hibernate.

---

### Post by Illua on 2010-04-07
I tried this, but it forze again not long after.
Its not that it goes into hibernation
Its as if someone had taken a print screen of what iwas looking at and then, i wont move, its a picture, no mouse no nothing.

---

### Post by ajgreeny on 2010-04-07
If you are using Visual Effects on the desktop, it is worth trying running with none, as compiz and ati graphics cards do not always get on too well together.

If that makes no difference, then apart from checking all the logs in /var/logs, and also including the old .xsession-errors.old in your home folder/partition, I have no idea how to help more.  It may, also be hardware related, eg bad memory module, or something similar, so try the memtest from your grub menu, let it run through at least a couple of times, and look for any errors that it finds, which will be noted at the bottom, if I remember correctly.

---

### Post by Comokanu on 2010-04-07
hmm...maybe change the theme to a less complicated theme or just turn off or downgrade your visual effects? Like lowering the color depth...I dunno sorry

---

