---
title: "Unable to boot Ubuntu"
date: 2009-12-24
forum: General Help
---

### Post by zweebna on 2009-12-24
Ok, so I dual boot Ubuntu 9.10 and Windows XP. A while back Windows got an error preventing me from booting it, and I had to system restore. Once I system restored, Windows works again. Huzzah. Except Ubuntu doesn't.

Normally when turning on my computer, there will be a screen showing my different OS's (that is, Ubuntu and XP), and I'd be able to choose one. After the system restore, however, this screen no longer shows up. Instead Windows boots up on it's own as if Ubuntu was never installed. When I tried to reinstall it, I saw there were already two partitions to my harddrive; one labeled Windows XP and the other labeled Ubuntu 9.10. 

Please help D:

---

### Post by oldfred on 2009-12-24
I assume you did not have a wubi install inside windows but on a separate partition?

You need to reinstall grub. If you did a clean install you have grub2, if an update from 9.04 you probably have grub legacy 0.97.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

or
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by gsmanners on 2009-12-24
EDIT: Never mind. See above.

---

### Post by zweebna on 2009-12-24
ok, now when I turn on my computer I get a screen showing:
[CENTER]

GNU GRUB version 1.97~beta4
[LEFT][  Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions. anywhere else TAB lists possible device/file completions.  ]

sh:grub


I must have done something wrong... T.T
[/LEFT]
[/CENTER]

---

### Post by oldfred on 2009-12-24
Try some of the suggestions by Herman in this link:
See herman's comments on OP with sh:grub and using command line
[http://ubuntuforums.org/showthread.php?t=1347583](http://ubuntuforums.org/showthread.php?t=1347583)

Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by zweebna on 2009-12-26
> **oldfred said:**
> Try some of the suggestions by Herman in this link:
See herman's comments on OP with sh:grub and using command line
[http://ubuntuforums.org/showthread.php?t=1347583](http://ubuntuforums.org/showthread.php?t=1347583) Ok 
this worked. Now how do I get it so I don't have to do this every time I want to boot?

---

### Post by oldfred on 2009-12-26
Once you are in your system, you can do an update of grub or the reinstall of grub.

```
sudo update-grub
```

This reinstalls grub and gives you a choice of what drive if you have more than one. You must know whether you want grub on sda, sdb, etc.

```
sudo dpkg-reconfigure grub-pc
```

---

### Post by zweebna on 2009-12-26
Thank you so so much Oldfred :D

---

