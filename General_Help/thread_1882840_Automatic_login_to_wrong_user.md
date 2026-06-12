---
title: "Automatic login to wrong user"
date: 2011-11-18
forum: General Help
---

### Post by geekman2 on 2011-11-18
After reverting back to natty when oneric didn't work properly, my automatic login settings where messed up.
Before I upgraded and then subsequently reverted my computer was set up so that it automatically logged into the other user, who is the primary user of the computer and not a power-user nor an administrator. But now, it is automatically logs in as me the administrator, thus making the computer unusable unless I give the other user my password, which I obviously can't do. What I would like to be able to do is either automatically log in as the other user or ask who you want to log in as at boot. please help

---

### Post by cbanakis on 2011-11-18
Well, I have not messed around with lubuntu...
But in Ubuntu, you can access the auto-login options by going to system/administration/log-in screen.

Or type "gdmsetup" in terminal.

There you can choose the default user to auto-login.

Hope this helps

---

### Post by SteveDee on 2011-11-18
> **geekman2 said:**
> ...What I would like to be able to do is either automatically log in as the other user or ask who you want to log in as at boot...

Assuming you are using Lubuntu, use you file manager to navigate to: /etc/xdg/lubuntu/lxdm
Then select from the file manager toolbar: Tools > Open Current Folder as Root.

After entering your password, a second file manager window will open.
Now right-click on lxdm.conf and open with your text editor.

The top of this file will look something like this:-
```

[base]
autologin=geekman2
session=/usr/bin/startlubuntu
# numlock=0
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

```
You can either change the "autologin=" name to the other user (so it auto logs into his account), or put a # in front of "autologin" so the system boots to the login screen.

---

