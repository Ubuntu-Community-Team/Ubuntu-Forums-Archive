---
title: "ubuntu-grace problems"
date: 2009-09-15
forum: General Help
---

### Post by pellao on 2009-09-15
hi. I recently installed ubuntu 9.04 (64 bits) in a quad core with a samsung lcd monitor. I have some preoblems with a program for XY graph. This program is XMGRACE. The problem is quite strange. The axis labels appears corrupted. a black or blue backgroubnd appears and it is imposible to me to fixed!
Any help is welvome. sorry for my english!

---

### Post by nvjopsddhapnv on 2009-10-16
I have recently upgraded my system to 9.04 and I am also getting the same problem. Can anybody please help to fix it??

---

### Post by nvjopsddhapnv on 2009-10-16
Here is a screen shot of Xmgrace windows 
[IMG]http://img261.imageshack.us/img261/8103/xmgrace.jpg[/IMG]

---

### Post by pellao on 2009-10-16
edit (as su) your xorg.conf
The device section must be something like

Section "Device"
    Identifier    "Configured Video Device"
        Option "EXAOptimizeMigration" "true"
        Option "MigrationHeuristic" "greedy"
EndSection

good luck (make backup before)

---

### Post by nvjopsddhapnv on 2009-10-17
Thank you very much it is working fine now. Here is the screenshot after fixing the problem. 
[IMG]http://img26.imageshack.us/img26/8103/xmgrace.jpg[/IMG]

---

