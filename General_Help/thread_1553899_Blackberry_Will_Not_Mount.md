---
title: "Blackberry Will Not Mount"
date: 2010-08-15
forum: General Help
---

### Post by Dportner on 2010-08-15
every since the upgrade to 10.04 iv had trouble mounting my blackberry tour...

when i connect it, it charges, the clock shows up and so on

also when i do "lsusb" ```
Bus 002 Device 004: ID 0fca:8004 Research In Motion, Ltd. 
```
shows up.


for now i have had to restart my computer every time i want to mount my blackberry. but once i disconnect it and try to plug it back in without restarting computer it will not mount


iv searched everywhere for an answer and am getting very desperate :(
please help


*EDIT*
k so solved this myself.
found the solution: [https://answers.launchpad.net/ubuntu/+question/109180](https://answers.launchpad.net/ubuntu/+question/109180)
simply rename /usr/sbin/bcharge  to /usr/sbin/bcharge.bak
and youre good to go

---

### Post by PBrn46 on 2010-08-26
i love you.

---

