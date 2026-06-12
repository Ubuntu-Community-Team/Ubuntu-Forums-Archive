---
title: "After updaing w no longer shows users"
date: 2011-10-14
forum: General Help
---

### Post by Coyote23 on 2011-10-14
Hello all, I have a simple problem. After upgrading to Xubuntu 11.10 this morning if I open a terminal and run w it shows 0 users logged in - normally, I'd see myself twice. It gives the same result if I run it with sudo too. 
While not a critical problem any help in fixing this will be greatly appreciated, 
thanks,

Coyote23

Update:

I did some digging, apparently w reads /var/run/utmp for user activity. I ran chkrootkit and it flagged up this (note: I don't have any reason to suspect a rootkit is at play, but I remembered seeing output related to that file a while back)

```

jon@Wolf:~$ sudo chkrootkit -q

/usr/lib/libreoffice/basis3.4/program/.services.rdb /usr/lib/pymodules/python2.7/.path /usr/lib/jvm/.java-1.6.0-openjdk.jinfo

eth0: PACKET SNIFFER(/sbin/dhclient[1226])
user jon deleted or never logged from lastlog!
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1291 tty7   /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
! jon          5711 pts/0  bash
! root         7983 pts/0  /bin/sh /usr/sbin/chkrootkit -q
! root         8512 pts/0  ./chkutmp
! root         8514 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         8513 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root         7982 pts/0  sudo chkrootkit -q

```If i cat the file however, it spits out gibberish. Interestingly enough, if I press Ctrl-Alt-F1 and do a console login... W works just fine, I think it may be a bug of sorts.

---

### Post by crdlb on 2011-10-14
There are bugs filed for this:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297)

[https://bugs.launchpad.net/lightdm/+bug/871070](https://bugs.launchpad.net/lightdm/+bug/871070)

---

### Post by Coyote23 on 2011-10-14
> **crdlb said:**
> There are bugs filed for this:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297)

[https://bugs.launchpad.net/lightdm/+bug/871070](https://bugs.launchpad.net/lightdm/+bug/871070)

Ah, I see. Thanks for pointing those out :)

How do I mark this as resolved?

Coyote23

---

