---
title: "create file of of all files being accessed"
date: 2011-01-09
forum: General Help
---

### Post by bdemers on 2011-01-09
I would like to create a listing of ALL files that are accessed during a session, start up to shut down.  This doesn't need to be real time, however, it would be better for me if it were.

```
find / -atime +1
``` will find all files that haven't been accessed for 1 day. If I control the environment properly, it'll tell me what I need to know, but it would take until the date rolled over for this line to be functional.  Be nice if I could work a bit quicker than that.  Any ideas?

---

### Post by andrewc6l on 2011-01-10
You might want to use
```
-amin -3 
```
(for files changed in the last 3 minutes).

If you like life to be a little more edgy (with possibility of file system damage, but that's all part of the game):
1. shut down to single user mode
2. ```
touch /home/mydir/myfile
sync
```
3. power off, or better yet use the [magic sysreq]("http://en.wikipedia.org/wiki/Magic_SysRq_key") RSB (not REISUB)

then use -anewer /home/mydir/myfile

Of course, this will cause fsck to be run (which may bring in other code that doesn't "normally" run on a reboot.)

---

