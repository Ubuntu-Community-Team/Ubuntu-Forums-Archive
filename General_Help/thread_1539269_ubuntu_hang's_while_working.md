---
title: "ubuntu hang's while working"
date: 2010-07-26
forum: General Help
---

### Post by xpluto on 2010-07-26
gnome does not respond for 5-20 seconds but mouse moves around but i can't click on anything some time the panel's fade for seconds 
i have these application's open: 
pidgin 2.6.6 , 
firefox 3.6.7 with these add-ons "stumble! ,add-block  plus,download helper ,no script,quick proxy, skip screen"
,evolution mail 2.28.3


i have 4 gig ram and i don't think caused by low ram or CPU  :(

---

### Post by xpluto on 2010-07-27
help!

---

### Post by dino99 on 2010-07-27
few checks:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

into : system admin hardware driver: check that the driver is activated

more info can be found into logs: 
- .xsession-errors (/home, ctrl+h to unhide it)
- system - admin - logviewer

---

### Post by P4man on 2010-07-27
also have a look at the output of ```
dmesg
``` after you had a freeze like that to see whats going on while it was "frozen"

---

### Post by xpluto on 2010-07-28
i have updated my Ubuntu  i think problem is fixed :popcorn:

---

