---
title: "X Server won't start after editing config file"
date: 2006-05-21
forum: General Help
---

### Post by Reef2006 on 2006-05-21
I'm a newbie to Ubuntu and messed up my system good.  I edited /etc/X11/xorg.conf  by commenting out the mouse drivers.  I was doing this because my synaptics touchpad in a Dell C400 laptop is erratic and I had found some info that this can be due to the pass-through track point messing up the interrupts.  I think the track point uses the mouse drivers and I wanted to disable it.  In any case, now I cannot boot back up in order to re-edit the configuration file.  When I try to boot,  X server gets disabled. I tried recovery mode but it still could not boot.  I can get to a command prompt, enter my logon info okay but then if I try to edit a file from there it cannot be viewed.  I thought about trying to use a live CD to get around this problem but am not sure if that would work.  Is there any other way to edit the configuration files?

---

### Post by deanjm1963 on 2006-05-21
a quick and easy way to get your xorg.conf back to the way it was

start up ubuntu and as you say you'll end up at a login screen

login with your username and password

after that type

> sudo su and hit enter and type your password in

then

> cd /etc/X11 hit enter

then

> cp xorg.conf~ xorg.conf hit enter

you might get a warning that you're overwriting a file, its ok, it's only a backup file thats created when ever you edit any text file.

log out and reboot

hope this helps... worked for me a few times

---

### Post by Reef2006 on 2006-05-21
Totally awsome.  Your fix worked like a champ!  Thank You!!!  I like to tinker with settings so I will definitely keep it around for my future mess ups.  Thanks again.

---

