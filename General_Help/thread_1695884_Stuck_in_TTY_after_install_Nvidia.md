---
title: "Stuck in TTY after install Nvidia"
date: 2011-02-26
forum: General Help
---

### Post by justinwood on 2011-02-26
Stuck in tty after installing a Nvidia driver. I've gone through all of the steps in [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1659287](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1659287) including the last problem where it temporarily freezes on the load screen. However there wasn't any documentation after that point. 

Notes for readers:

Pressing Cntrl Alt F7 just sticks me to a stuck screen and not the GUI.

Any suggestions?

---

### Post by alzie on 2011-02-26
Do you know where the download of the nVidia file is?  Mine was on the desktop.

After logging in at the terminal,

```
cd Desktop

sudo /etc/init.d/gdm stop

sudo sh .N[tab].run  
```
(tab is to use the autocomplete)

choose x.org auto config in the install program

sudo reboot

If I remember correctly, the installation complained at some point about something but I clicked to go ahead anyway.

The instructions I used to install the driver are from here: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

After the successful install of the drivers follow the instructions here: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

The second set of instructions will prevent a kernal upgrade from messing up your driver and dropping you back at the terminal. 

I hope this helps

---

