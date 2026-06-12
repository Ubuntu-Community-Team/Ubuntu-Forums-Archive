---
title: "Possible Nautilus Error"
date: 2010-04-25
forum: General Help
---

### Post by miniCruzer on 2010-04-25
I received this odd error when opening gedit from the terminal. gedit opened, but this error worries me:
```

sam@vicarious:~/Programming/C++$ gedit calculator.cpp 
_IceTransSocketUNIXConnect: Cannot connect to non-local host ubuntu
_IceTransSocketUNIXConnect: Cannot connect to non-local host ubuntu

(gedit:5930): EggSMClient-WARNING **: Failed to connect to the session manager: Could not open network socket

sam@vicarious:~/Programming/C++$ 

```I guess it would be more of a warning than an error. I've Googled it, and not much returned that was readable.

------

After changing the hostname, you need to reboot your machine. That fixed it

---

### Post by dcstar on 2010-04-26
> **miniCruzer said:**
> I received this odd error when opening gedit from the terminal. gedit opened, but this error worries me:
```

sam@vicarious:~/Programming/C++$ gedit calculator.cpp 
_IceTransSocketUNIXConnect: Cannot connect to non-local host ubuntu
_IceTransSocketUNIXConnect: Cannot connect to non-local host ubuntu

(gedit:5930): EggSMClient-WARNING **: Failed to connect to the session manager: Could not open network socket

sam@vicarious:~/Programming/C++$ 

```I guess it would be more of a warning than an error. I've Googled it, and not much returned that was readable.

------

After changing the hostname, you need to reboot your machine. That fixed it

Gedit is a GUI application that is not meant to be launched from a command line unless you are debugging a problem.

Anything you see that does not affect its operation comes under the category of "Big deal".

---

### Post by gamebasewan on 2010-04-26
I has another kind of  Nautilus Error

[http://ubuntuforums.org/showthread.php?t=1462694](http://ubuntuforums.org/showthread.php?t=1462694)

---

### Post by cyber-monk on 2010-08-04
I started getting this error after changing my hostname (both in /etc/hosts and /etc/hostname).  Try looking at ~/.ICEauthority -- this file is mostly unreadable.  Check for an out of date hostname.  If it looks like your hostname is being cached do the following:

```
1) Check the contents of /etc/hosts and /etc/hostname to have the correct hostname.

2) Delete your ~/.ICEauthority

3) Restart your networking: /etc/init.d/networking restart
   or 
   Simply reboot.
```

Worked for me on Ubuntu 10.04 i386 desktop.

---

