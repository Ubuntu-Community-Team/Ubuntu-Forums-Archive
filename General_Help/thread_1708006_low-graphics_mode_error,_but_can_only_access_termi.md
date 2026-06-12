---
title: "low-graphics mode error, but can only access terminal"
date: 2011-03-16
forum: General Help
---

### Post by snigwel on 2011-03-16
Right, so, I posted this earlier in what may have been the wrong category, but my issue remains this: I have a dell inspiron mini 1012 running ubuntu netbook edition. I left it open running photorec, and when i returned everything had slowed down immensly, so i restarted. Now when i try to start the computer, after the dell startup screen it goes to a black screen with a cursor up top, then flashes a screen of some more text a few times [the same text it appears, though too fast to proerly read -- "setting sensors limits..."], then the "running in low-graphics mode" pops up. from there i am given options to run in low graphics mode, reconfigure graphics, troubleshoot, exit to console login, or restart x. all are unresponsive except the console login.
 
would love any help! 
 
-chris

---

### Post by sikander3786 on 2011-03-16
Did you remove your existing xorg.conf file before reconfiguring the graphics?

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

---

### Post by snigwel on 2011-03-16
sikander -- none of the "reconfigure graphics" options seem to have any effect.  When I select them and then hit 'ok,' it merely reverts to the same menue with the top option re-selected by default.  Dunno what that implies, but I will try your suggestion once I get home (am at an internet cafe atm) and will report the results.
 
thanks!
 
-c

---

### Post by sikander3786 on 2011-03-16
Removing the older xorg.conf allows dpkg to reconfigure xserver according to the current detections as modern X is capable of configuring graphics on the fly and doesn't need any configuration files any more.

Note the capital 'X' in 'X11'. The commands are case sensitive.

The commands would return you to the command prompt and it is only a reboot that would tell us the outcome of those.

Hope your issue will be solved soon.

---

### Post by snigwel on 2011-03-16
hrm.  so, when i try to move the original file, it is not recognized -- "mv: cannot stat '/etc/X11/xorg.conf' : No such file or directory"

i tried the remaining commands anyhow, but there was no change.  still says that it is running in low graphics mode upon startup, but when the "what would you like to do" menu pops up the Run ubuntu in low-graphics mode forjust one session" option causes a "stand by one minute while the display restarts..."dialog to flash a number of times before remaining up, after which, when i click ok i am left with a black screen with an unresponsive cursor blinking away.  

thanks for your help thus far!

-c

---

### Post by sikander3786 on 2011-03-17
At the login screen, click your username and Session menu will appear in the bottom of the screen. Can you select 'GNOME' or 'ubuntu-desktop' from that and login?

---

### Post by snigwel on 2011-03-17
unfortunately there is no login screen as such.  After the dell startup screen it flashes a few imes between black and the "setting sensor limits" text as if it's trying to do something, followed by the must run in low-graphics mode dialog, which, once ok is clicked, brings me to the "what would you like to do" menue with the various largely ineffective options listed earlier.

---

### Post by sikander3786 on 2011-03-17
Can you actually see the Desktop if you choose to run it in low graphics mode? If so, once you are on the Desktop, logout and you'll see the login screen.

---

### Post by snigwel on 2011-03-18
no, unfortunately never get to the desktop. when i select the option to go into low-graphics mode, the screen flashes between black and a "sand by one minute while the display restarts..." dialog box as if it is indeed trying to enter low-graphics mode.  afterflashing a few times in this manner, the dialog box remains up, but when i click ok the diakog box simply disappears, leaving a black screen with a flashing, yet unresponsive, cursor.

---

