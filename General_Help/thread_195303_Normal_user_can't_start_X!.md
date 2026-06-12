---
title: "Normal user can't start X!"
date: 2006-06-12
forum: General Help
---

### Post by wr0x2 on 2006-06-12
Last session, I was copying a large game and had to change its permissions so that my regular user account could access them. The changes from chmod and chown were not showing in nautilus, and I couldn't access the files. So, of course, I rm -r /tmp as root, hoping that this might freshen things up. Obviously I had to kill X and restart. Well, now I can't login to X. It gives me an error about GDM not being able to write to my home dir. I can login to X running gnome as root, and I viewed the permissions of my home dir, they give my regular user full rights. My root FS, which has /home on it has 80gb free, so I don't think that freespace is the problem. Also, I can kill the X login window and login as my regular user through a console. I get some errors about not being able to access files though when I try to start x... Did my permissions somehow become corrupted?

---

### Post by zxee on 2006-06-12
When I've had this problem in my slack install this was my solution:
> cd /home   chmod 700 yourusername chown yourusername yourusername  chgrp yourusername yourusername
Of course you can always create a new user and move everything to that account.
Hope that helps.

---

### Post by wr0x2 on 2006-06-12
Did this, but I suppose my permissions were fine because I tried logging in again and it still failed. Message was that GDM could not write to my authorization file.

---

### Post by wr0x2 on 2006-06-12
OK, I think I'm getting somewhere. I looked at the permissions for my .Xauthority file, and it belonged to root. I chowned and chgrp'd it to myself and set perms to 700, and when I try to login, I get a different error, that being that my session lasted less than 10 seconds blah blah. Here's what was in my .xsession-errors file:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:1.Xservers" -h "" -l ":1" "wr0x2"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

```

EDIT: Got it working. See [this]("http://www.ubuntuforums.org/showthread.php?t=177301&highlight=mkdtemp%3A+private+socket+dir%3A+Permission+denied") thread.

---

