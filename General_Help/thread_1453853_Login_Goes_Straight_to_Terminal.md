---
title: "Login Goes Straight to Terminal"
date: 2010-04-13
forum: General Help
---

### Post by edelrosario on 2010-04-13
Hi, so I'm somewhat new to Ubuntu, well anyways here's what happened:
     I was on my netbook and I accidently ran Warsow, so I just clicked quit.  After I clicked quit my netbook froze.  I waited a good 5minutes or so, but nothing happened and I could do anything.  I had no choice but to do a hard shutdown.  After I turned the netbook back on everything seemed normal.  It went to the login screen and everything, but after I click on my username and type in my password I just get a terminal in the top left portion of my screen.  I've googled for a good hour and could not find a solution that worked.  Please help me! :(  

BTW:  I'm running UNR 9.10 and if you need more info let me know!  I appreciate the help.

---

### Post by Pikestaff on 2010-04-13
Have you tried ```
startx
```

Failing that, have you tried reconfiguring xorg?

```
sudo dpkg-reconfigure xserver-xorg
```

Edit:

Another one to try:

```
sudo /etc/init.d/gdm start
```

---

### Post by edelrosario on 2010-04-13
> **edelrosario said:**
> Hi, so I'm somewhat new to Ubuntu, well anyways here's what happened:
     I was on my netbook and I accidently ran Warsow, so I just clicked quit.  After I clicked quit my netbook froze.  I waited a good 5minutes or so, but nothing happened and I could do anything.  I had no choice but to do a hard shutdown.  After I turned the netbook back on everything seemed normal.  It went to the login screen and everything, but after I click on my username and type in my password I just get a terminal in the top left portion of my screen.  I've googled for a good hour and could not find a solution that worked.  Please help me! :(  

BTW:  I'm running UNR 9.10 and if you need more info let me know!  I appreciate the help.

i did sudo startx i get the following:
Fatal server errror:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org)
ddxSigGiveUp:  Closing log

when I do sudo dpkg-reconfigure xserver-xorg nothing happens

when I do sudo /etc/init.d/gdm start i get:
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start
Since the script you are attempting to invoke has been coverted to an Upstart Job, you may also use the start(8) utility, e.g. start gdm

Edit:  I tried sudo service gdm start and sudo start gdm and I get:
start: Job is already running: gdm

---

### Post by edelrosario on 2010-04-13
UPDATE:  I did
```
sudo gnome-session
```
it got me to my desktop and everything, but my panel is missing (where it has all the open programs, time, where you click to shutdown/restart/etc.)

---

### Post by Pikestaff on 2010-04-13
> **edelrosario said:**
> UPDATE:  I did
```
sudo gnome-session
```
it got me to my desktop and everything, but my panel is missing (where it has all the open programs, time, where you click to shutdown/restart/etc.)

Did a quick Google and found a few promising things you could try:

[http://www.raasukutty.com/blog/open-source/ubuntu-panel-missing.html](http://www.raasukutty.com/blog/open-source/ubuntu-panel-missing.html)

and

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by utnubuuser on 2010-04-13
Try > sudo killall gnome-panel
That'll restart the panels

---

