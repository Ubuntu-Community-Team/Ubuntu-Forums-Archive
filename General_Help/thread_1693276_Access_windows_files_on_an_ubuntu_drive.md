---
title: "Access windows files on an ubuntu drive?"
date: 2011-02-22
forum: General Help
---

### Post by UBuntinator on 2011-02-22
I Have two drives, one with windows and one with ubuntu, is it possible to access my files that iv'e put on the drive with windows
from ubuntu, because all i see c:/ and Filesystem?

windows vista 32 bit
ubuntu 10.10
acer computer

---

### Post by TeoBigusGeekus on 2011-02-22
Of course...
What do you mean by "...all I see is c: and filesystem"?

---

### Post by UBuntinator on 2011-02-22
On Windows i Have c:/ and d:/ on ubuntu i have c:/ and filesystem i want to use d:/ same physical drive, but ubuntu thinks of as just ubuntu and vice versa on windows, i would like to use d:/ not filesystem.

---

### Post by TeoBigusGeekus on 2011-02-22
Have you gone to the Places menu?
Can't you locate your hard drive in there?
Don't expect it to have the same name as in windows (d, e, f, g, etc.); just pay attention to the sizes mentioned there (50gb volume, 100 gb volume) in order to find it.

---

### Post by atti84it on 2011-02-22
you should be able to see your disks when you click on the top menu "places".
you will not find "C:\" but names like "25Gb disk"

---

### Post by UBuntinator on 2011-02-22
Theres no files from windows in filesystem...

---

### Post by TeoBigusGeekus on 2011-02-22
What's in the 640gb disk?

---

### Post by UBuntinator on 2011-02-22
thats the combined size of my two drives, but i cant find my d:/ files in it...

---

### Post by TeoBigusGeekus on 2011-02-22
Go into File System>/media folder. What's in there?

---

### Post by oldfred on 2011-02-22
Did you install wubi in the d: drive which really is a partition not another hard drive?

Post this:

sudo fdisk -lu

---

### Post by Syed75 on 2011-02-22
Places<File System<Host

---

