---
title: "firefox printing flash"
date: 2010-04-03
forum: General Help
---

### Post by marranzano on 2010-04-03
hello,
I'm trying to print this sudocu flash by right clicking on it and telling flash to print it:

[http://fantavillage.repubblica.it/gdm/index.php?page=playsudoku&id=20100403_03&ck_fantacalcio=BADSESSION](http://fantavillage.repubblica.it/gdm/index.php?page=playsudoku&id=20100403_03&ck_fantacalcio=BADSESSION)

everything is ok with midori.

with firefox I get the message asking me to choose printer but no printer shows.
in terminal I get:
```
sh: lpstat: Permission denied
```

so I added this to apparmor:
```
 # flashplugin
  /usr/bin/lpstat ix,
```

Now when i ask firefox to print that flash it asks me for a printer and the correct printer shows up but once i choose it firefox crasces.
in terminal i get:
```
firefox: ../../src/xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

as i said before midori works ok so i believe it's a ff issue.

[ubuntu 9.10 x64, 2.6.31-21-generic, ff 3.5.8, Shockwave Flash 10.0 r32]

ideas?
thanx
Marranzano

---

### Post by marranzano on 2010-04-04
same applies for flash 10.0 r45

---

### Post by nlucaroni on 2010-09-30
Hey Marranzano.

I had the same problem. I did what you said, and modified the apparmor profile without any problems. I also needed to add lines for the google talk plugin --checking the /var/log/kern.log showed me all the denied access issues to resolve.  Thanks for your solution!

Ubuntu 10.4 LTS 64bit
Flash - 10.2 d161
Firefox - 3.6.10

*EDIT:* adding the googletalk plugin directory crashed firefox on opening gmail or other services that utilized the plugin. Since I don't use it, or haven't in awhile, I've just left the denied access to it.

```
Inconsistency detected by ld.so: dl-open.c: 611: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
```

---

