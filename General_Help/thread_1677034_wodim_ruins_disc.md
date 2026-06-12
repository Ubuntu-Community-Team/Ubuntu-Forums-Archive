---
title: "wodim ruins disc"
date: 2011-01-28
forum: General Help
---

### Post by doru001 on 2011-01-28
wodim dev=/dev/scd0 -v -multi -data cdimage.iso
used to work for me in Ubuntu Desktop 10.04 LTS, but now, after a few automatic updates, renders "empty" discs which are reported as corrupted by Nero under Windows. The whole writing process takes place normally, just as shown in this similar thread: [http://ubuntuforums.org/showthread.php?t=1496781&highlight=wodim](http://ubuntuforums.org/showthread.php?t=1496781&highlight=wodim)

Should I worry about this: [http://ubuntuforums.org/showthread.php?t=1292559&highlight=wodim](http://ubuntuforums.org/showthread.php?t=1292559&highlight=wodim)

Any suggestion welcomed, 
Doru

---

### Post by doru001 on 2012-05-07
The solution is here: [http://ubuntuforums.org/showpost.php?p=11833837&postcount=26](http://ubuntuforums.org/showpost.php?p=11833837&postcount=26)

---

### Post by Neodarkness on 2012-06-26
Just dropping by to confirm that wodim indeed sucks. Replacing it with cdrecord and mkisofs fixed my long standing (multi-distro and multi-laptop) brasero inability to burn cd's without ruining them. 
Hope anyone else looking for a solution to brasero's problems finds this (much faster than I did).

---

