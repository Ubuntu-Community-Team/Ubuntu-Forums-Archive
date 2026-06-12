---
title: "gdm doesn't start! help!"
date: 2006-04-17
forum: General Help
---

### Post by vbmaster on 2006-04-17
I was happily surfing on my dapper system, and I didn't turned it off for two days, so I don't known what caused the problem, but the fact is that I can't get  the gdm working, only the console version. But by making startx I can get into dapper.

The gdm log has this:

> 
Couldn't open RGB_DB '/usr/share/X11/rgb'

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux ubuntu 2.6.15-20-386 #1 PREEMPT Tue Apr 4 17:48:51 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Mon Apr 17 20:27:57 2006
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /etc/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server


Can anybody help me?

(the log of X does not appears to return errors)

---

### Post by aysiu on 2006-04-17
If startx works, try this ```
sudo /etc/init.d/gdm restart
```

---

### Post by vbmaster on 2006-04-17
[QUOTE=aysiu]If startx works, try this ```
sudo /etc/init.d/gdm restart
```[/QUOTE]

I have already tried that, and just simply fails.

I rebooted my pc, before that error, because I had actualize the xgl and compiz version from 0.0.2 to 0.0.9.

But the problem shouldn't be that. (i think...)

---

