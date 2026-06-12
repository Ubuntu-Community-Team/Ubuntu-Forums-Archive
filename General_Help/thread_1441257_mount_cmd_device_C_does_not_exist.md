---
title: "mount cmd device C does not exist"
date: 2010-03-28
forum: General Help
---

### Post by ken poy on 2010-03-28
Hi again,  i am still trying to get DOSBOX running.  i do get DOSBOX and download the 
OLDDOS EXEC  from windows.  
my next step is to issue a mount cmd
sudo mount c /home/ken/QBasic        the QBasic code is in a folder in home/ken directory

now i get special device c does not exist???

searching the web i did find references to a similar problem which referenced the
ETC/FSTAB  directory  so did a ls and have nothing there.

do not know where device c is or should be???         thanks ken

---

### Post by bobcollard on 2010-03-28
> **ken poy said:**
> Hi again,  i am still trying to get DOSBOX running.  i do get DOSBOX and download the 
OLDDOS EXEC  from windows.  
my next step is to issue a mount cmd
sudo mount c /home/ken/QBasic        the QBasic code is in a folder in home/ken directory

now i get special device c does not exist???

searching the web i did find references to a similar problem which referenced the
ETC/FSTAB  directory  so did a ls and have nothing there.

do not know where device c is or should be???         thanks ken
Dev c is what you named the first character in your command line.  However, Linux does not define drives as c or d, that is a windows designation.  dev/sda1 or dev/sda2 is closer to what you may be looking for.  With both drives plugged in try to run this in Terminal, it will tell you what you have and give you a hint what to put into place instead of c
```
sudo df -h
```

---

