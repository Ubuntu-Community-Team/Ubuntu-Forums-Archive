---
title: "Can't get to the GUI!?"
date: 2010-01-08
forum: General Help
---

### Post by westnj on 2010-01-08
Hello everyone i'm a a linux newbie using ubuntu 9.10 karmic koala. I recently updated my system using the update manager and installed all the recommended files and updates. my computer then automatically rebooted but when it turned back on I found that I am stuck on a console looking like screen. I can log in with my username and password, can move around using the simple commands I know (cd, ls), can reboot and shutdown, but cannot get to the GUI!

I searched online and found <CTRL> <ALT> <F7>. All of the text disappears and I am left with a flashing underscore at the top of the screen but nothing else. When I press <CTRL> <ALT> <F1> it switches back to the console.

Any help would be much appreciated! Thanks!

---

### Post by Leppie on 2010-01-08
issue the following command:
```
startx
```
this will initiate an xwindows session.

---

### Post by dearingj on 2010-01-08
1) What happens when you type in this command? Specifically, do you see any error messages?
```
sudo service gdm restart
```

2) Try checking for updates again, using these two commands.
To check for updates, assuming you're connected to the internet:
```
sudo aptitude update
```

To install any updates:
```
sudo aptitude safe-upgrade
```

---

### Post by westnj on 2010-01-08
I tried startx, I screen flashes for a couple of seconds then goes back to the console with two errors

(EE) Failed to laod module "i810" (module does not exist, 0)
Setting Master
(EE) config/hal: couldn't initialize context: unknown error (null)

waiting for X server to shut down Dropping master
 ddxSigGiveUp: Closing log

Any ideas?

---

### Post by Leppie on 2010-01-08
sounds like something messed up your xorg.conf, try removing it:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
then retry startx

---

### Post by westnj on 2010-01-08
I tried 

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

but get the message

mv: cannot stat '/etc/X11/xorg.conf' : No such file or directory

---

### Post by westnj on 2010-01-08
When I try

sudo service gdm restart

I get the message

restart: Unknown instance:

---

### Post by Leppie on 2010-01-08
install the intel drivers for x:
```
sudo apt-get install xf86-video-intel
```

---

### Post by westnj on 2010-01-08
I get the message

```
E: Couldn't find package xf86-video-intel
```

---

### Post by Leppie on 2010-01-08
and this one:
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by westnj on 2010-01-08
Tried that it says that ```
xserver-xorg-video-intel is already the newest version
```

Thanks for your patience Leppie

---

### Post by warfacegod on 2010-01-08
```
sudo apt-get remove gdm
```


```
sudo apt-get install gdm
```

---

### Post by westnj on 2010-01-08
When trying to remove gdm got

```
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
dpkg: erro processing gdm (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 indicator-session
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by warfacegod on 2010-01-09
Looks like you need a guru. I was getting similar messages yesterday on my wife's desktop. I fixed it by reinstalling going from 8.10 to 9.10



Off Topic:
  Good grief Leppie, didn't you have like 300 something beans last week?

---

### Post by westnj on 2010-01-09
Thanks anyway

---

### Post by Leppie on 2010-01-09
> **warfacegod said:**
> Good grief Leppie, didn't you have like 300 something beans last week?
i think it was something like 500... but really OT... LOL

---

### Post by Leppie on 2010-01-09
> **westnj said:**
> When trying to remove gdm got

```
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_new
dpkg: erro processing gdm (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 indicator-session
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

try the following:
```
sudo dpkg-reconfigure gdm
```
if it doesn't give any errors, try startx again.

---

