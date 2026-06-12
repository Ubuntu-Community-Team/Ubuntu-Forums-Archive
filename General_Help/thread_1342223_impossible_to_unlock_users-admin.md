---
title: "impossible to unlock users-admin"
date: 2009-11-30
forum: General Help
---

### Post by jy_moustache on 2009-11-30
Hi

I'm using Ubuntu 9.10 Karmic Koala and a problem occured recently.
When I try to run users-admin, whether it is from system->administration->users & groups or from a console, I cannot unlock it. The key icon is not greyed but when I click on it, nothing happens.

when I run gksudo users-admin, it works fine and the key icon has disappeared (which seems normal).

I've looked for several solutions but nothing worked.
I am in the admin, root, policykit groups.

does anyone have any idea ?

thank you
jy

---

### Post by sisco311 on 2009-11-30
Hi and welcome to the forums!

Go to System -> Administration -> System Monitor -> Processes tab and see if *polkit-gnome-authentication-agent-1* is in the list of process. 

Or run:
```
ps -ef | grep -v grep | grep polkit-gnome-authentication-agent-1
```
in a terminal (if nothing is returned the process is not running).

If it's not in the list of precesses, then start it. Press Alt+F2 and run:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

Go to System -> Administration -> Users and Groups and try the unlock button, this time it should work.

Then make sure that /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 is automatically started at login time (System -> Preferences -> Startup Applications).

If  /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 is running but the unlock button still doesn't work, then run:
```
pkexec echo "test"
```
in a terminal. An authentication dialog should pop up, if not post the error message displayed by the command.

---

### Post by jy_moustache on 2009-12-01
Hi

making sure policykit was running did the trick.
everything is working fine now

thanks a lot for your help !

jy

---

### Post by dnoyeb on 2010-03-17
Im having the same problem but my polkit is running.  It used to work.  Then I tried to change the username by renaming it in passwd and group and shadow and gshadow.

Then I blew away my home directory.  When the new one was created, i could no longer use the unlock icon.  Anyway, I don't care about that user, so I fixed it generally, but then added a new user and defined him as an administrator.  That new user can not use the unlock icon either.  Can't figure it out.

I just figured this out after over  a year for my 8.10.  its already happened to 9.10 but I can't figure it out because the system is now changed...

---

