---
title: "file manager problem in GNOME"
date: 2010-05-30
forum: General Help
---

### Post by kerryh8er04 on 2010-05-30
It just started today after my system froze I did a hard restart and now when I boot up into gnome I have dozens of "starting file manager" screens and I can no longer see the desktop, also most programs wont open up. It will show in the task bar "starting X" and that is it, it closes the program.

---

### Post by Jeroensum on 2010-06-01
Sounds like a messed up profile :)

Just switch to a non-graphical tty (ctrl+alt+F2) and login.
Now add a new user:  sudo adduser newusernamehere  and fill in the forms
Next, check your current groups by issuing:  groups
This should list something like:
jeroensum adm dialout cdrom plugdev lpadmin admin

Add (all) these groups to the new account like so:
sudo usermod -G adm dialout cdrom plugdev lpadmin admin newusernamehere

Now that you have a fresh user account, restart all desktop activity by restarting gdm:  /etc/init.d/gdm restart

Your screen will flicker a bit, kind of like it's not sure what to do now and will then present you with the graphical login prompt, this should take a few seconds but no more than half a minute.

Login with your new account and check if all is well, if you want you can use sudo and chown to copy and re-own the files from your old account. (for things like evolution _copy_ (if things go wrong you have a backup) the .evolution directory and re-setup your accounts.

---

