---
title: "Latest Updates Crashed my 10.04"
date: 2010-10-23
forum: General Help
---

### Post by planetofdeviants on 2010-10-23
I just was notified of updates today (October 23, 2010).  I installed them.  The updater froze when it sent a message saying it exited with an error.

I was unable to open other applications.  Firefox or terminal would bring up a window, but it was blank.

The main menu worked, so I chose restart.

I think it now only boots to what is called safe mode?

I get these messages in a terminal only type gui:

- Target filesystem doesn't have /sbin/init

- No init found.  Try passing init=bootarg

- Can't open /root/dev/console: no such file

- Kernel panic - not syncing:Attempted to kill init

- pid: 1 comm: init Tained: G          D 2.2.6.32.-25-generic #45-ubuntu

Any help appreciated to rescue.  I spent a lot of time getting things tweaked the way I want them.

---

### Post by planetofdeviants on 2010-10-23
Apparently some inodes needed fixing?


1. I booted a live cd and started Terminal.

2. I typed in this command and ran.

```
e2fsck -f -y -v /dev/sdb1
``` 

 I answered yes to fixes.

3. I rebooted.


I got everything back.  Whew!  That was a scare.

---

