---
title: "ummm...can't log in after install"
date: 2006-06-17
forum: General Help
---

### Post by rockatship on 2006-06-17
hey there
seem to have run into a silly problem. i'm at the 6.06 log in screen after a fresh install, and I can't log in. I don't seem to remember there being any screen during the install that was asking me for a username, and I can't use root, so...is there something I'm missing here?
thanks
dan

---

### Post by Ramses de Norre on 2006-06-17
You aren't asked to give any username or password??
Can you boot into recovery mode? If so you might be able to fix it from there with the adduser command (I'll explain how if you can get to recovery).

---

### Post by rockatship on 2006-06-17
booting to recovery now
i was asked for the root password, but not a general username as usual. i was installing half-mindedly, so i wasn't paying much attention to things, but i've installed ubuntu a dozen times before and don't think i would have / could have missed the username screen...bizarre
but yes, if you could help me with adduser, i would very much appreciate it

---

### Post by rockatship on 2006-06-17
actually i just figured it out (pretty simple command!)

thanks

---

### Post by rockatship on 2006-06-17
hmmm now how do i go about enabling root login from recovery?

---

### Post by Ramses de Norre on 2006-06-17
You were asked for a root password? You did an expert install or something then? Ok uhm you should be able to log in as root in normal mode too then in a tty (ctrl-alt-F1), there do adduser --home /home/user_name user_name && adduser user_name admin.
I don't know whether your going to be in all necessary groups then, log in with the new user and do groups to check.
I'm in ```
user_name adm dialout cdrom floppy tape audio dip video plugdev lpadmin scanner admin
``` with a user created by the installer.

---

### Post by mscman on 2006-06-17
NOTE: Many people on these forums (including myself) discourage the practice of enabling root login.  This is simply telling you how to do it, not recommending it.

If you want to enable root login from gdm, you'll have to edit the file /etc/gdm/gdm.conf-custom

In recovery mode, run the command:
```
nano /etc/gdm/gdm.conf-custom
```

and under the [security] section, add the line:
```
AllowRoot=true
```

This also assumes you did have to enter a root password during install.  If you didn't enter a root password, you'll have to run the command:
```
passwd root
```
to set one.

---

