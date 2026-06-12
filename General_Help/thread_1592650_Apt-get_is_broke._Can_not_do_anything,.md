---
title: "Apt-get is broke. Can not do anything,"
date: 2010-10-10
forum: General Help
---

### Post by cgroza on 2010-10-10
Hello everyone. Today i tried to remove icongen but it turned into an error. Now i can not do anything with apt, dpkg,aptitude. It returns the following error:  "E: Sub-process /usr/bin/dpkg returned an error code (1)"

Here is the complete output:  
```

cgroza@cgroza-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icogen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 23.7GB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 279189 files and directories currently installed.)
Removing icogen ...
rm: cannot remove `/usr/share/icoGEN/data/': No such file or directory
dpkg: error processing icogen (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 icogen
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks.

---

### Post by cgroza on 2010-10-10
Please some one answer. I can't even upgrade. That error keeps getting in the way all the time, it just stops everything.

---

### Post by ninjamogzero on 2010-10-10
See: [http://ubuntuforums.org/showthread.php?t=1566679](http://ubuntuforums.org/showthread.php?t=1566679)

Another user had the same problem and found a workaround - hope it helps.

---

### Post by cgroza on 2010-10-10
Ok, i am on my way of trying this. Thank you.

---

### Post by cgroza on 2010-10-10
YES! It works. THANK YOU !

---

### Post by ninjamogzero on 2010-10-11
No problem. Enjoy the upgrade :-)

---

### Post by cgroza on 2010-10-11
I see you upgraded too. Enjoy.

---

