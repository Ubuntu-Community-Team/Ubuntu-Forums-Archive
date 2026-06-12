---
title: "How to launch upon boot ?"
date: 2006-06-20
forum: General Help
---

### Post by weasel fierce on 2006-06-20
How do I set an application in KDE, so it will boot automatically, when I boot up the computer and KDE ?

I found a nice, quake-style console program, that I really like, but its a bit less handy, if you have to open a regular console first to launch that program

---

### Post by Jucato on 2006-06-20
are you talking about YaKuake?
To make YaKuake start on boot, go to your ~/.kde/Autostart folder, right-click and choose New > Shortcut to Application. In the General tab, type in a name for the shortcut. In the Applications tab, put the app name in the proper field, and in the Command field, put in /usr/bin/yakuake (presuming you were referring to yakuake) or any other program you'd like to launch at startup.

Take note that this will only apply to your user account.

---

### Post by mlind on 2006-06-20
You can probably assign shortcut key for it to make access easier.
I guess you could start it on kde lauch by putting it on ~/.kderc or shortcut on ~/.kde/Autostart folder

---

### Post by weasel fierce on 2006-06-20
yeah, its yakuake.

Thank you so much :) Im still pretty new to KDE

---

### Post by weasel fierce on 2006-06-20
The only problem I have with it, is that it isnt translucent. 

When I launch it from the regular konsole, I get the following:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Uh oh.. can't write data..


It works just fine,and lets me execute commands, but apart from the bottom line, its just plain white.

EDIT: Nevermind, I figured out how to change options. It seems to work fine, though that error makes me wonder

---

