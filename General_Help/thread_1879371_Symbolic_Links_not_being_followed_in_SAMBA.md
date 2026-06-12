---
title: "Symbolic Links not being followed in SAMBA"
date: 2011-11-11
forum: General Help
---

### Post by kooldino on 2011-11-11
It looks like I can't follow symbolic links...

I tried putting the following links in both the smb.conf and the usershares:

>  follow symlinks = yes
 wide symlinks = yes
 unix extensions  = no

No luck.

---

### Post by blueridgedog on 2011-11-11
So symlinks in the shared directory work? 

I think the syntax is:

follow symlinks = yes
wide links = yes

Try the above, restart samba and test.

---

### Post by kooldino on 2011-11-22
> **blueridgedog said:**
> So symlinks in the shared directory work? 

No, that's the problem.

> I think the syntax is:

follow symlinks = yes
wide links = yes

Try the above, restart samba and test.

It doesn't work.

---

### Post by kooldino on 2012-01-05
Still having this issue.

---

### Post by kooldino on 2012-01-13
bump

---

### Post by oldfred on 2012-01-13
I use symlinks and often suggest them, but Morbius1 corrects me for those using Samba that it does not follow symlinks and it is better to use bind.

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by Derek Karpinski on 2012-01-13
bindfs is broken in 11.10.

Symbolic links work for me with Samba.

---

