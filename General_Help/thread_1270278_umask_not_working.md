---
title: "umask not working"
date: 2009-09-19
forum: General Help
---

### Post by alexlaban on 2009-09-19
I've uncommented and set the umask to 0002 in both .profile and etc/profile restarted the system and still it doesn't work, if I run umask in the terminal it returns "0022". Why is this, I can't see that I've done anything wrong.

---

### Post by Brandon Williams on 2009-09-19
Are you using gdm as your login manager? If so, then this _should_ be working, since /etc/gdm/Xsession will source both /etc/profile and $HOME/.profile if they exist. I'm not sure whether other display managers also do this. All display managers should respect .xprofile, though, since it is sourced from one of the files in /etc/X11/Xsession.d/, so you could try this:
```
ln -s ~/.profile ~/.xprofile
```

If that suggestion doesn't help, then launch another instance of bash from the command line with:
```
bash -l
```
This will run bash as a login shell, which means that the profile files should be sourced. When you do this, what is the umask? If it's still not right, then there is something wrong with the changes to profile and/or .profile and you should post those files so we can tell you what it is. If the umask is correct when you do this, then look at the preferences for your terminal emulator and make sure that it is running the shell as a login shell. This will solve the problem in the terminal emulator, but not for graphical programs launched from the menu.

---

