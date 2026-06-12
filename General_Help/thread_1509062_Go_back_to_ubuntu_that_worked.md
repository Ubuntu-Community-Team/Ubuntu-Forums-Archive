---
title: "Go back to ubuntu that worked"
date: 2010-06-13
forum: General Help
---

### Post by dudedeland on 2010-06-13
I have Ubuntu 10 with Windows xp, how do I go back to ubuntu 9.1? I can't get past the black screen and don't want to mess with it anymore. :guitar:

---

### Post by tom.swartz07 on 2010-06-13
Reinstall using the iso for 9.10.

Thats all you really could do?


If you describe exactly what the problem is, perhaps we could resolve it, so you dont lose all of your data..

---

### Post by WorMzy on 2010-06-13
I think you mean 9.10. You can download it here: [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

---

### Post by cbecker78 on 2010-06-13
use a live cd to backup data in /home.  Save it somewhere besides your partition that ubuntu is installed.  Copy the entire /home directory.  Now reinstall version 9.10.  When it comes to partitioning/formating... choose manual, and do not reformat the partition.  Just skip past that step.  doing it this way, you will most likely get 9.1 back as a fresh install, and all of your data and custom settings will still be in place.  You will only need to go back and install all of your extra programs.

^^I have done this sucessfully, if you are lucky, it will work fine, and you can toss the backup of /home you made into the closet and forget about it until your HD fails permanently.  If not lucky, then a good thing you have that backup!

In the future, consider having /home on a separate partition, and if possible, two partitions for /root: one for your current install, and the second for the next install...

---

