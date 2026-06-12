---
title: "GUI disable, command lines only"
date: 2006-05-04
forum: General Help
---

### Post by cajunaggie on 2006-05-04
This morning I updated my system using the update manager. I recieved a message saying that since the kernel had updated I should reboot my machine as quickly as possible. I saved everything, rebooted and waited for it to load up to the login screen.

Unfortunately that never happened. Instead of going to the GDM, my computer pops up with a command line login. Gnome Breezy ttyl or something along those lines. I rebooted it thinking that perhaps it was a glitch, but no dice. Something disabled my GUI. Does anyone know how to restore it? I have to work through the command line only at this point, so please be detailed in any instructions you leave. I'll gladly provide any other information you need. 

Until then, ](*,)

EDIT: As an experiment I tried putting comands in. When I tried pulling up Firefox, I was given an error message that said GTK could not be loaded. Not sure if that helps.

---

### Post by JoeMetal on 2006-05-04
Try ```
startx
```

---

### Post by harishg on 2006-05-04
did you try to  use the recover mode.?

---

### Post by cajunaggie on 2006-05-04
[QUOTE=harishg]did you try to  use the recover mode.?[/QUOTE]
Yes, to no avail. Same status

---

### Post by cajunaggie on 2006-05-04
[QUOTE=JoeMetal]Try ```
startx
```[/QUOTE]

Thank you, this brings back my GUI. 

My next question is how I can make that permanent, instead of having to manually run startx

---

### Post by cajunaggie on 2006-05-27
*bump* :rolleyes: 
Normally when booting up my system, it goes straight to the GDM where I can then login. For some unknown reason, now when I boot up my computer, it goes to a command-line login. After logging in, I can bring up the GUI with this the "startx" command.

How do I fix this? What part of the system do I need to be poking around to fix this? Somewhere in GRUB? Elsewhere?

---

### Post by Sutekh on 2006-05-27
Try this command to setup the GDM
```
sudo dpkg-reconfigure gdm
```
Then use
```
sudo /etc/init.d/gdm start
```
to start it

---

### Post by sinkxdie on 2006-05-27
Just to tell you cajunnaggie, you can just seach next time. This has been answered many times, it was even my first question. :D

---

### Post by cajunaggie on 2006-05-27
[QUOTE=sinkxdie]Just to tell you cajunnaggie, you can just seach next time. This has been answered many times, it was even my first question. :D[/QUOTE]
I figured it had been, unfortunately for me, I suck at creating search queries. My wording is awful. I do appreciate this community putting up with all my crap. I love this place. :mrgreen:

---

### Post by cajunaggie on 2006-05-28
[QUOTE=Sutekh]Try this command to setup the GDM
```
sudo dpkg-reconfigure gdm
```
Then use
```
sudo /etc/init.d/gdm start
```
to start it[/QUOTE]

Looks like I somehow uninstalled my GDM. A reinstallation and a reboot fixed. Thanks for the help! :)

---

### Post by Sutekh on 2006-05-28
[quote=cajunaggie]Looks like I somehow uninstalled my GDM. A reinstallation and a reboot fixed. Thanks for the help! :)[/quote]
That'll do it.  Glad you got it working now.

---

