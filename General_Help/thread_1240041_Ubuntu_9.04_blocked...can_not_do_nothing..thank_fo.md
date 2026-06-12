---
title: "Ubuntu 9.04 blocked...can not do nothing..thank for help"
date: 2009-08-14
forum: General Help
---

### Post by mirkko22 on 2009-08-14
hello

I am totally blocked after Ubuntu and gnome load...Impossible to start application or do something...I can just run a terminal with a keyboard shortcut but don't know what to do...When typing something teh texte are typped in opposite...For example if I type HELP the display is PLEH...

In fact when Grub start I get a lot strange character like [[D^ [[D^ [[D^ [[D^ [[D^ [[D^ in all lines (where the list of services are displayed under black screen...all services are market OK)

Any suggestion ??

many thank

---

### Post by Couto on 2009-08-14
> **mirkko22 said:**
> hello

I am totally blocked after Ubuntu and gnome load...Impossible to start application or do something...I can just run a terminal with a keyboard shortcut but don't know what to do...When typing something teh texte are typped in opposite...For example if I type HELP the display is PLEH...

In fact when Grub start I get a lot strange character like [[D^ [[D^ [[D^ [[D^ [[D^ [[D^ in all lines (where the list of services are displayed under black screen...all services are market OK)

Any suggestion ??

many thank

What are you trying to do?

---

### Post by mirkko22 on 2009-08-14
Nothing...I try to just use my PC like always...What I have forget to say is my PC was with screensaver active...When I have moove the mouse for start tp work the problem have start...impossible to do something...I have restart but no change...

Maybe is a screensaver problem because before my screensaver was set to start after 30 min but never start...I have ask help and some people tell me to do "gnome-screensaver start" and after that my scrensaver was ok and start to be enabled after 30 min...This always work for many days...until today... :-(

---

### Post by lisati on 2009-08-14
> **mirkko22 said:**
> Nothing...I try to just use my PC like always...What I have forget to say is my PC was with screensaver active...When I have moove the mouse for start tp work the problem have start...impossible to do something...I have restart but no change...

Maybe is a screensaver problem because before my screensaver was set to start after 30 min but never start...I have ask help and some people tell me to do "gnome-screensaver start" and after that my scrensaver was ok and start to be enabled after 30 min...This always work for many days...until today... :-(

I'm curious. Is English your second language?

---

### Post by mirkko22 on 2009-08-14
no third language :-) First are french, second italian and fourth spanish....Sorry am not speak well...I just write like I feel...never learn english at school...

---

### Post by gastly on 2009-08-14
Maybe your monitor got 'flipped'? Dunno how it could be, but it seems like it if you're saying that if you type 'HELP' it says 'PLEH'.

You can do this...once you're at the login screen, type Ctrl+Alt+F2, this will let you login into a simple commandline environment. From there you can do anything...try reinstalling drivers for your monitor/graphics card and see if it works.

Also, try restarting X:
```
sudo /etc/init.d/gdm restart
```

---

### Post by P4man on 2009-08-14
if I understand you right, even your grub menu has corrupted.. graphics/characters ? In that case, I think your videocard  is on its way to PC heaven :S

If its a desktop you can try opening your case and making sure its plugged in right (push it hard). also check if your fan is running. doesnt sound like a software problem tho, unless I misunderstood your post

---

### Post by 3rdalbum on 2009-08-14
It sounds like the left arrow on your keyboard is stuck down, or that the keyboard or BIOS erroneously believes that it is recieving "key down" messages constantly.

Try shutting down your computer entirely, and then starting it back up.

---

### Post by mirkko22 on 2009-08-14
It seem the problem come from my keyboard/mouse wireless Logitech Wave.... If I use a standard device I don't have problem.... Is probably a bug with last update and my xorg.conf are probably wrong....I will investigate....

thank

---

