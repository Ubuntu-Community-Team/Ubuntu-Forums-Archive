---
title: "ubuntu-bug Segmentation fault!"
date: 2010-12-22
forum: General Help
---

### Post by 65 mustang on 2010-12-22
Ok, so i want to report a bug against empathy.  As many times before i run ubuntu-bug.  But it segfaults.  I tried running it on itself and firefox more segfaults.  I cant report any bugs!  My system is up to date and i tried rebooting.  Help!  Can anyone else report bugs?

```

tsmith@wopr:~$ uname -a
Linux wopr 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
tsmith@wopr:~$ ps ax | grep empathy
 3124 ?        Sl     0:10 empathy
 3825 pts/0    R+     0:00 grep --color=auto empathy
tsmith@wopr:~$ ubuntu-bug 3124
Segmentation fault
tsmith@wopr:~$ ubuntu-bug empathy
Segmentation fault
tsmith@wopr:~$ ubuntu-bug ubuntu-bug
Segmentation fault
tsmith@wopr:~$ ubuntu-bug firefox
Segmentation fault

```

---

