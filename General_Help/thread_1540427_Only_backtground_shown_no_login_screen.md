---
title: "Only backtground shown no login screen"
date: 2010-07-27
forum: General Help
---

### Post by devdimi on 2010-07-27
Hi everyone,

I have dual boot Windows/Ubuntu 9.10 and everything was running fine until recently when after booting to Ubuntu just showed me the system background image with mouse pointer and that was it - no login screen, nothing.

I tried swithing to console mode and logging in - it works fine, but swithing back to x just gives me the background image and the mouse pointer  ( it is working though )

Any ideas or help will be appretiated.

Regards

---

### Post by arrrghhh on 2010-07-27
I'm assuming you've restarted the workstation?  Does it still occur?  Have you tried restarting GDM?

---

### Post by devdimi on 2010-07-27
OK - this did the trick until next system reboot and than its the same.
After restarting x I get errors like:
"The panel encountered a problem while loading OAFIID:GNOME_ClockApplet".

---

### Post by arrrghhh on 2010-07-27
Have you changed anything recently?  Upgrades, changes to video drivers, etc?

---

### Post by linux18 on 2010-07-27
boot-splash and Plymouth screens limit useful output so you'll have to go through a long list of commands:
================================================================



STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

``` and login

STEP 4:
-then type:
```

 xinit

```STEP 5:
-when xinit starts type:
```

metacity &

```- for ubuntu OR:
```

compiz &

```- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```- for xubuntu

STEP 6:
-then type:
```

 gnome-panel & 

```-for ubuntu OR:
```

 xfce4-panel & 

```-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```-for networking
===============================================================

then see if apt can fix it:

```

 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"

```

I've really got to get a shorter script!

---

### Post by Monkeystador on 2010-08-09
I had something similiar, the login screen just didnt appear. Just the background was visible. In my case ubuntu 10.04 wasnt done checking on one of my usb memory sticks (some error). Until that check timed out or i removed the mem stick nothing happened. 
Afterwards everything was fine.

---

