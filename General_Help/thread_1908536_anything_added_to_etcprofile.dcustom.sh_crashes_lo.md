---
title: "anything added to /etc/profile.d/custom.sh crashes login"
date: 2012-01-13
forum: General Help
---

### Post by randoma on 2012-01-13
Hi, 

I just installed Ubuntu 11.10, and added some custom environment variables and shell functions via some silly script under `/etc/profile.d` (for all users). But right after logging out, I can not log back in:  I select my user name, enter the password, authentication seems to succeed, the login screen flickers as if loading, but right before the desktop shows, the screen goes blank, and I am thrown right back at the login screen.  I tried default Ubuntu, Ubuntu 2D, as well asGNOME, and GNOME Classic, all the same issue. 

The ssh logins are successful. 

If I remove the custom script under `/etc/profile.d` the local logins work fine.  If I simplify the custom script to:

```

foo () { echo I am foo; }

```

save as `/etc/profile.d/foo.sh`, the logins crash.  

If the script contains variable definitions only (and no bash specific constructs), the logins work, and variables are defined on a terminal as expected. 

There was no such issue with previous version of Ubuntu I've used. 

I appreciate any pointers, hint, or reports if you can reproduce the issue.

Thanks, 

Nick Stokes

---

### Post by ZorkMaster on 2012-05-24
Is there an **exit 0** line at the bottom of your script?  I was having the same problem as you, but after removing that line it starting working.

---

