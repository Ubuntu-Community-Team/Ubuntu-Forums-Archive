---
title: "Cannot log in to GNOME after crash, only GNOME failsagfe works"
date: 2010-02-05
forum: General Help
---

### Post by karmakowski on 2010-02-05
After a crash I cannot log in to the GNOME environment anymore, after entering the password the login animation is being displayed for a while and then screen returns to gdm. GNOME failsafe works fine. I don't know what information may be useful to debug this problem. ~/.xsession-errors contains
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/ssh-agent: error while loading shared libraries: libkrb5support.so.0: cannot open shared object file: No such file or directory
```

libkrb5support.so.0 seems to be missing:
```
$ ls -l /usr/lib | grep libkrb5support
lrwxrwxrwx   1 root root       21 2010-01-14 10:37 libkrb5support.so.0 -> libkrb5support.so.0.1
```

I tried moving away .config/ .gconf/ and .gconfd/, it didn't help. 

What should I do to get the GNOME back?

---

### Post by karmakowski on 2010-02-05
Reinstalling MIT Kerberos runtime libraries (libkrb5-3) and MIT Kerberos runtime libraries - Support library (libkrb5support0) solved this problem.

---

