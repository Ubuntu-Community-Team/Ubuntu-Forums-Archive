---
title: "inotify/max_user_watches permission denied"
date: 2010-03-26
forum: General Help
---

### Post by jlbprof on 2010-03-26
I am wanting to use inotify_wait in some scripts, and following the directions I need more then 8192 watches.

The directions say to do

echo 32768 > /proc/sys/fs/inotify/max_user_watches

When I do I get permission denied

so I make the jump to warp

sudo echo 32768 > /proc/sys/fs/inotify/max_user_watches

and get permission denied again.

How does a mere mortal sudoer change this value?

Thanx

Julian

---

### Post by talz13 on 2010-04-28
I need help with this too... I have three folders that I am watching, and am running out of inotify watches.

```
$ sudo cat 16384 > /proc/sys/fs/inotify/max_user_watches
-bash: /proc/sys/fs/inotify/max_user_watches: Permission denied
$ sudo -i echo 16384 > /proc/sys/fs/inotify/max_user_watches
-bash: /proc/sys/fs/inotify/max_user_watches: Permission denied
```
etc....

---

### Post by talz13 on 2010-04-30
I found an answer!

[http://www.mail-archive.com/factor-talk@lists.sourceforge.net/msg03967.html](http://www.mail-archive.com/factor-talk@lists.sourceforge.net/msg03967.html)

> Try increasing the watch limit before starting Factor:

sudo sysctl fs.inotify.max_user_watches=65536

Slava



I used the 'sudo sysctl' method and no permission denied error!

---

