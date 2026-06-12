---
title: "New HDD, home folder encryption and ddrescue"
date: 2010-12-20
forum: General Help
---

### Post by GrzesiekC on 2010-12-20
Hi all,

I am planing swap mine old HDD with new one. W will be cloning with ddrescue and then resize by gParted. Only concern is mine home folder which is encrypted now.

Do I have to make any special steps to clone old HDD.

Cheers
Grzesiek

---

### Post by Mr.Kappa on 2011-01-20
Did you have anyproblems in doing that or are you still waiting for a response? ;)

---

### Post by GrzesiekC on 2011-01-20
Hi,

I figured it out by mine self in virtual test-bed. :-)

Boot from CD, turn on universe repository in source manager. Then I have used ddrescue tool:

sudo apt-get install ddrescue
ddrescue -v /dev/sda /dev/sdb - remember that disk order is very important with this command. 

In my case:

sda - source HDD with encrypted home folder
sdb - target HDD clean disk

This tool will make ideal copy of source HDD. All encrypted date will be intact and fully accessible after disk swap. 
At the end, you can resize partition on target HDD with gParted if desire.

Good luck and Cheers
Grzesiek

---

