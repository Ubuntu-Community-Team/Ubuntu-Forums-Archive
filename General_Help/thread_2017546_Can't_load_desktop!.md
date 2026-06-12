---
title: "Can't load desktop!"
date: 2012-07-05
forum: General Help
---

### Post by popppppz on 2012-07-05
Hi, I am having a problem loading the desktop of Kubuntu. I see the Kubuntu 12.04 loading screen, then I go to a black screen with a mouse cursor then my screen turns blue. I do have a mouse cursor but can only right click, but nothing will actually work. I can however press alt + ctrl + F1 and get into a terminal. I have tried reinstalling xorg xsessions x11 my intel graphics card and commands like plasma-desktop and xstart but nothing has worked. The problem started after I installed screenlets and rebooted. The only error message I've seen is when I type plasma-desktop;
 
unable to autolaunch a dbus-daemon without a $display for x11
 
I have also tried falling back to an older kernal, running check disk, sudp apt-get remove screenlets (which said it removed it), and repairing packages. 
 
Any advice or help would be appreciated, thank you. 
 
Kubuntu 12.04 fully updated to newest kernal.

---

### Post by Redblade20XX on 2012-07-05
If you can get into the terminal, type this,
```
cat /var/log/Xorg.0.log | grep EE
```
and post the output.

-Red

---

### Post by popppppz on 2012-07-05
(WW) warning, (EE) error,  (NI) not implemented, (??) unknown. 
[     43.622] (II) Loading extension MIT-SCREEN-SAVER
 
 
Thats what I got when I typed it.

---

### Post by popppppz on 2012-07-05
Problem solved, I loaded to grub, highlighted the first kernal, then pressed e, I then found the line quiet boot, and right after that I added nomodeset, the rebooted using Ctrl + x, after that I pressed logout of Ubuntu when it failed to load, switched to KDE Fail Safe then relogged in.  I then deleted screenlets, problem solved.  Thank you.

---

