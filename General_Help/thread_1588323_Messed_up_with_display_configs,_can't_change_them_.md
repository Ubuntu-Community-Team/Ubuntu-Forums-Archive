---
title: "Messed up with display configs, can't change them back!      ](*,)"
date: 2010-10-04
forum: General Help
---

### Post by afk46 on 2010-10-04
Hello,

I recently tried to plug my laptop to a TV and adjusted the settings consequently. The thing is now that I want to use it with the laptop screen. I can barely see the first top inch... I'm pretty shure it has something to do with the display configuration since it works flawlessly when I log in as a guest.

Is there a way for me to reset the screen to it default config without using my regular session?

Thanks, I'm really stuck for now.

Jim

---

### Post by Crazedpsyc on 2010-10-04
Theres howto here that I think can help you:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
to run the commands there run the 
```
gksudo /etc/init.d/gdm stop
``` part after pressing Alt+F2 to get a run dialog and the screen will darken and you should enter your password
also try looking at the xrandr command
```
man xrandr
```

---

### Post by smilodonis on 2010-10-04
Try this:
you should boot your linux into safe mode, using the grub menu and  selecting the safe mode option - the second from the top usually.

there you get a command line interface with root logged in. type the following there:

 	Code:
 	sudo dpkg-reconfigure xserver-xorg 
this will guide you through keyboard mouse and display settings. when done reboot by hitting ctrl+alt+del

---

### Post by afk46 on 2010-10-04
WOrked like a charm. Thank you very much!

---

