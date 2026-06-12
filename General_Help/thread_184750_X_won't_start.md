---
title: "X won't start"
date: 2006-05-30
forum: General Help
---

### Post by statto on 2006-05-30
Hello, I recently upgraded a computer from Warty to Breezy, but its been plagued with problems since then. When it starts up, instead of opening the graphical login screen, I get a shell login. If I try and start a graphical login session (Ctrl+Alt+F7) I'm told that'I cannot start the X server (your graphical interface). It is likely that it is not set up correctly.'

When I view the X server output it just displays

*/etc/X11/X is not executable*

I'm not much good at using the command line interface, so I'm pretty stuck as to what to do. Hope someone out there can help me.

---

### Post by SavageBeginner on 2006-05-30
This will step you through reconfiguring the xserver.

In Terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by statto on 2006-05-30
I tried that already and I get told *xserver-xorg is not installed*

When I try to install the package I get told that it has a big list of dependencies which aren't going to be installed. Hmm.

---

### Post by SavageBeginner on 2006-05-30
Can you post the contents of /etc/apt/sources.list?

---

### Post by bruce89 on 2006-05-30
```
sudo apt-get install ubuntu-desktop
``` will install X, and all other Ubuntu things.  How were they missing?  Did you do a server install?

---

### Post by statto on 2006-05-30
Alright, I installed ubuntu-desktop, but I'm getting a very similar thing still. The difference is instead of getting ```
/etc/X11/X is not executable
``` I get nothing

Also, I get told my xcommon-xorg is broken or not fully installed, rather than being not installed.

my sources.list is

```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy multiverse
```

---

