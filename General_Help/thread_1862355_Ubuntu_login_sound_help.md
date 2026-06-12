---
title: "Ubuntu login sound help"
date: 2011-10-16
forum: General Help
---

### Post by MidnightFirepaw on 2011-10-16
Hey, I've recently installed ubuntu 11.10 (I've been using ubuntu since 9.04) And I've been wondering how to change the login sound. Not that it's annoying, but I prefer to customize it. I don't mind opening configuration files and stuff.

---

### Post by MidnightFirepaw on 2011-10-16
bump. Come on.. can't be that hard. and google is failing me

---

### Post by dcstar on 2011-10-17
> **MidnightFirepaw said:**
> bump. Come on.. can't be that hard. and google is failing me

Look harder:

[https://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Disable-Change-Login-Sound](https://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Disable-Change-Login-Sound)

---

### Post by MidnightFirepaw on 2011-10-17
*blinks* That certainly did not turn up for me, thanks!

---

### Post by haqking on 2011-10-17
> **MidnightFirepaw said:**
> *blinks* That certainly did not turn up for me, thanks!

For 11.10

[http://maketecheasier.com/disable-login-sound-in-ubuntu-oneiric-quick-tips/2011/09/15](http://maketecheasier.com/disable-login-sound-in-ubuntu-oneiric-quick-tips/2011/09/15)

[http://blog.fromagique.com/disabling-the-stupid-login-sound-on-ubuntu-11](http://blog.fromagique.com/disabling-the-stupid-login-sound-on-ubuntu-11)

[http://ubuntuforums.org/showthread.php?t=1807626](http://ubuntuforums.org/showthread.php?t=1807626)

---

### Post by darkwalt on 2011-10-18
Easy solution:

```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

change NoDisplay=true to NoDisplay=false

```
sudo apt-get install sox libsox-fmt-mp3
```

Go to startup applications.  Uncheck Gnome login sound.  Create a new startup program

```
play /dir-name/soundname.extension
```

Tested and true solution for me from 10.4 - 11.10.  Works better for me because I can use any audio file that sox plays.

---

