---
title: "Run levels."
date: 2010-08-24
forum: General Help
---

### Post by zozza on 2010-08-24
I understand the basics of run levels but there are a few things I do not understand.

1.  My understanding is that when Ubuntu boots up it uses a particular number of scripts from the /etc/rc[number].d directory which link to the scripts in the /etc/init.d directory.  *Runlevel* shows I am using 2.

My rc2.d, rc3.d, rc4.d, and rc5.d directories are identical.  But if I wanted to change the runlevel how do I do this.  If I do *init 4* then now *runlevel  *shows "2 4".  What does this "2 4" mean?

2.  I understand the relevance of all directories and files except for rcS.d which contains the following scripts

rwxrwxrwx 1 root root  21 2010-08-08 20:10 S13pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx 1 root root  16 2010-08-08 20:10 S25brltty -> ../init.d/brltty
lrwxrwxrwx 1 root root  18 2010-08-08 20:10 S37apparmor -> ../init.d/apparmor
lrwxrwxrwx 1 root root  20 2010-08-08 20:10 S47lm-sensors -> ../init.d/lm-sensors
lrwxrwxrwx 1 root root  17 2010-08-08 20:10 S55urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  21 2010-08-09 11:10 S65firestarter -> ../init.d/firestarter
lrwxrwxrwx 1 root root  24 2010-08-08 20:10 S70screen-cleanup -> ../init.d/screen-cleanup
lrwxrwxrwx 1 root root  20 2010-08-08 20:10 S70x11-common -> ../init.d/x11-common

What is the point of this directory and its files?

3.  It seems that the documentation I have read is non specific to Ubuntu e.g. references to /etc/inittab which does not exist in Ubuntu.    This ([FONT=Helvetica, Arial, sans-serif]https://help.ubuntu.com/community/UbuntuBootupHowto) for example, is not very detailed.  Can someone suggests some helpful newbie-ish information for Ubuntu?

Thanks!
[/FONT]

---

### Post by quizno50 on 2010-08-24
I've always been slightly confused at the way Ubuntu boots myself, but if you want to change runlevels you just have to use the telinit command:
```
telinit [desired runlevel]
```
As far as I know when init spits back numbers at you that's the run level your in, I've personally never seen it give me two numbers before.
the rcS.d directory *should* be the directory that contains the scripts to init on boot.
Dunno if this helps much, but maybe it'll point you in the right direction?

---

