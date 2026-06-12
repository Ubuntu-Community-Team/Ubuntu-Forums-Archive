---
title: "Corrupt file breaking package manager"
date: 2012-03-07
forum: General Help
---

### Post by bobman321123 on 2012-03-07
Every time I try to use the package manager, whether for updating, installing, removing, etc, it always fails. It all seems to point to this package....

```
(Reading database ... 272925 files and directories currently installed.)
Removing composite-2012 ...
rm: cannot remove `/usr/autodesk/Composite_2012': No such file or directory
dpkg: error processing composite-2012 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 composite-2012
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How do I fix this?

---

### Post by raja.genupula on 2012-03-07
```
sudo dpkg --configure -a
sudo apt-get install -f
```

now try again , what its giving to you ?

---

### Post by bobman321123 on 2012-03-07
```
josh@caesar:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  composite-2012
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 499 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 272925 files and directories currently installed.)
Removing composite-2012 ...
rm: cannot remove `/usr/autodesk/Composite_2012': No such file or directory
dpkg: error processing composite-2012 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 composite-2012
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by raja.genupula on 2012-03-07
what about the first one ? that one also useful .

---

### Post by bobman321123 on 2012-03-08
The first command gave me no output. I ran the first one before the second one.

---

### Post by raja.genupula on 2012-03-09
ok do this 
```
sudo mkdir /usr/autodesk/Composite_2012
```
then try again with what you wanna do . 

all the best . Let us know what you got .

---

### Post by bobman321123 on 2012-03-09
How it looks right now.... that seemed to fix it.
Thanks a bunch, man. You're a huge help. :D

---

