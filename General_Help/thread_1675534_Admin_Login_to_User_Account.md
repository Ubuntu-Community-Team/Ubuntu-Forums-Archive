---
title: "Admin Login to User Account"
date: 2011-01-25
forum: General Help
---

### Post by segallis on 2011-01-25
I have several PC's running Ubuntu/Gnome at home.  I am wondering if there is a way as admin that I can log into one of my kid's user accounts with an admin/root password.  I realize thru a terminal I can use sudo to gain access to any files, but I want to be able to run from the desktop occasionally.

The only solution I know of right now is to set a password that we both know (I'd prefer to let them pick their own since we've had issues with them logging into someone else's account), or to reset their password when I want access.  I'd prefer a simple temporary override sort of like sudo does in a terminal.

Thanks,
-G

---

### Post by sisco311 on 2011-01-26
You can use sudo/gksudo to run any application as another user.

To switch to user **uname**:
```
sudo -u **uname** -i
<run commands as **uname**>
exit    #or press Ctrl+d
```

For GUI applications use gksudo:
```

xhost +SI:localuser:**uname**
gksudo -u **uname** -l "firefox"
gksudo -u **uname** -l "nautilus --no-desktop"
xhost -SI:localuser:**uname**
```

Or you can start a gnome-session on one of the virtual terminals:
```
sudo -u **uname** -i xinit /usr/bin/gnome-session -- :3 vt9
```
[noparse]The above code starts the session on vt9, so you can press Ctrl+Alt+F7 (or F8) and Ctrl+Alt+F9 to switch back and forth between the sessions.[/noparse]

---

