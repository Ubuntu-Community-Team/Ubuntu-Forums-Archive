---
title: "I'm a member of the right group yet file is still read-only"
date: 2011-10-13
forum: General Help
---

### Post by henrylaw on 2011-10-13
Ubuntu 10.04 server, running for ages, apparently all well apart from this.

There is a user "mas" set up to own an application package I've written.  It is in a group "mas".  
```
$ id mas
uid=1003(mas) gid=1003(mas) groups=1003(mas),1000(henry)
```My own user "henry" is also in that mas group:
```
$ id henry
uid=1000(henry) gid=1000(henry) groups=1000(henry),111(admin),1003(mas)
```The application has a log file /var/log/mas/mas.log which is owned by "mas" in the "mas" group:
```
$ stat /var/log/mas/mas.log
  File: `/var/log/mas/mas.log'  (lines snipped)
Access: (0664/-rw-rw-r--)  Uid: ( 1003/     mas)   Gid: ( 1003/     mas)
```And the /var/log/mas directory is also writable by the "mas" group:
```
(0775/drwxrwxr-x)  Uid: ( 1003/     mas)   Gid: ( 1003/     mas)
```And yet the log file /var/log/mas/mas.log is **read-only to me**, "henry".  For example if I use emacs to edit it I get "Note: file is write protected" on the bottom of the display.

The only thing that's odd -- confession time -- is that I recently changed the UID and GID of the "mas" user from what it used to be (1002), to match the UID and GID of a remotely-mounted NFS volume.  I used usermod and groupmod to do that.  I'm quite prepared to believe that that's what caused the problem, but I can't find the error and I'm completely stumped as to what to do next.  /etc/group and /etc/passwd look OK as far as I can see.

Anyone suggest what might be wrong?

---

### Post by stoneguy on 2011-10-13
Maybe existing files in /var/log/mas are still owned by 1002? Try chown'ing them to 1003 while su'd to root. File chown'ing is often required when changing uid/gid.

---

### Post by henrylaw on 2011-10-14
> **henrylaw said:**
> I recently changed the UID and GID of the "mas" user

... I rebooted overnight and it's OK now.  It seems that Linux caches information about GIDs which groupmod doesn't change.  Not unreasonable, I suppose, but I didn't know that.

One gets so used to not having to reboot Ubuntu when making changes (by contrast to that other OS, in which rebooting is the first thing you do when anything odd happens).

---

### Post by sisco311 on 2011-10-14
You don't have to reboot. Just start a new login shell (log out and log back in).

EDIT

from **info coreutils 'id invocation'**:
>    Primary and supplementary groups for a process are normally inherited
from its parent and are usually unchanged since login.  This means that
if you change the group database after logging in, `id' will not
reflect your changes within your existing login session.  Running `id'
with a user argument causes the user and group database to be consulted
afresh, and so will give a different result.


---

