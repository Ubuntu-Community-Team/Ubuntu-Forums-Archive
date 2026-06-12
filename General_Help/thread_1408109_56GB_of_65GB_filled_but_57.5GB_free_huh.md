---
title: "56GB of 65GB filled but 57.5GB free? huh?"
date: 2010-02-16
forum: General Help
---

### Post by JCG3 on 2010-02-16
i have a HP wx8000 with a scsi drive on it that has a max capacity of 65GB. my HDD reports that it has 57.5 Free. it also reports that i have 56.2GB used. i am really confused at this point. it was a brand new install 5 days ago. 

i have included two screen shots to help. 

thanks in advance

JCG3

---

### Post by iponeverything on 2010-02-16
are you getting sda1 and sdb1 mixed up?

---

### Post by JCG3 on 2010-02-16
nope. i know the diff. i right click on the local hard drive, click properties and the screen shoot is what i get. seems off doesn't it?

---

### Post by ironclaw on 2010-02-16
Nautilus is combining sda1 and sdb2 together in its count. df should be right.

---

### Post by JCG3 on 2010-02-16
yep your right turned my external off and logged out then logged back in. ran nautilus and it shows the size just like gparted reports. 

thanks ironclaw!

---

