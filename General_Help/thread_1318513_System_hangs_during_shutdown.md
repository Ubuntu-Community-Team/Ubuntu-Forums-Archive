---
title: "System hangs during shutdown"
date: 2009-11-07
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-11-07
I have a wubi install on a dell inspiron 1440. Ever since i upgraded to 9.10, the system hangs during shutdown/restart. Gets to "deactivating swap"..., than I get....

[20903.996142] Buffer I/O error on device loop0, logical block 1992818
[20904.996225] Buffer I/O error on device loop0, logical block 4644290
[20904.996303] Buffer I/O error on device loop0, logical block 3704228

---

### Post by Feelin_froggy8877 on 2009-11-07
Just thought I'd add, I do not have this problem on my desktop 
(full install)

---

### Post by schulznotee on 2009-11-07
Similar problems only line following "Deactivating swap" is
[130.192087] Buffer I/O error on device loop0, logical block 1215312

There had been more buffer i/o errors but multiple re-starts/shutdown have gotten me to this single line.

9.10, Compaq Presario C500 w/ max mem upgrade

---

### Post by Feelin_froggy8877 on 2009-11-07
It does seem to be wubi related. I had used "sudo shutdown -h now" shut down just fine. Hope this can be resolved, hate to have to open a term everytime I wanna shutdown.

---

### Post by CaKiwi on 2009-11-07
There is a problem if you upgrade from a Wubi installation.  I was pointed to this solution:

[https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589](https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589)   post #19

---

### Post by Feelin_froggy8877 on 2009-11-07
The link is no good. Ill keep checking around though.

---

### Post by CaKiwi on 2009-11-07
Try the link in post #10 here

[http://ubuntuforums.org/showthread.php?t=1308198&highlight=cakiwi](http://ubuntuforums.org/showthread.php?t=1308198&highlight=cakiwi)

---

### Post by Feelin_froggy8877 on 2009-11-07
I did find the post, Made the mods to the specified file.. Still have yet to try and shutdown.

(update) Fix from post #19 worked great.
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

