---
title: "Login only possible as root"
date: 2010-04-16
forum: General Help
---

### Post by ajoliveira on 2010-04-16
Hello

After today's sudo upgrade on Karmic amd64, I am able to login only as root on my xubuntu system. Tried to change password on my user account but the result is the same. Is anybody experiencing the same behavior?

Cheers

Antonio

---

### Post by Brandon Williams on 2010-04-17
Does this apply to console logins too? Or just to graphical logins?

Is it possible that the permissions on some file or directory in your home directory is preventing login? Run this command, where $USER is the username on the problem account:
```
find /home/$USER \! -user $USER
```
Are there any unexpected files in the listing?

And my final thought ... do you see any relevant error or warning messages in any of the log files? The most useful ones would probably be messages, deamon.log, auth.log, and user.log, though any other log file might have something if those don't.

---

### Post by ajoliveira on 2010-04-18
Hello Brandon

Thanks for your reply. I was talking about graphical login. I will take a short survey on permissions on the basis you suggest and will get back to you asap. Meanwhile I am using gnome as a graphic environment, and it is working as sought.

---

### Post by ajoliveira on 2010-04-20
Good morning

So I finally checked out the permissions, and .ICEauthority had root permissions.

sudo chown <user>:<group> ~/.ICEauthority

and that's it.

Gnome complained about the file but login went ahead, not xfce, xfce will not allow login.

Thanks for the tip, Brandon, I should suspect permissions right from the start.

---

