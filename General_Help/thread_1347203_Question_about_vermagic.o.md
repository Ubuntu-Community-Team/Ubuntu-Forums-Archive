---
title: "Question about vermagic.o"
date: 2009-12-05
forum: General Help
---

### Post by shariefbe on 2009-12-05
what is this vermagic.o where it is in root file system and what this object says?

---

### Post by RedSingularity on 2009-12-05
You can locate it by using the find command.......here you go


sudo find / -name vermagic.o

---

### Post by shariefbe on 2009-12-06
yes i already done this...but i didnt get any file name "vermagic.o"
see
```

sharief@sharief-desktop:~$ sudo find / -name vermagic.o
[sudo] password for sharief: 
sharief@sharief-desktop:~$ 
```

---

### Post by RedSingularity on 2009-12-06
What is it for anyway?

---

### Post by RedSingularity on 2009-12-06
You know what you can do.........use apt-file

sudo apt-get install apt-file

then....

sudo apt-file search vermagic

This will give you the package names that vermagic appears in.

---

