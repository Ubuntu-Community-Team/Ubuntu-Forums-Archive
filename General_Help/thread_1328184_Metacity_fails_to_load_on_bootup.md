---
title: "Metacity fails to load on bootup"
date: 2009-11-16
forum: General Help
---

### Post by juanmunoz on 2009-11-16
I installed compiz last night but didn't get it to work that well ,I installed and unistalled a couple of times .Form add and remove , also from terminal and finally fro synaptic manager. Now when I login , I can not see The borders on windows and can't minimize. I typed metacity in the terminal got thing right for awhile, but If i close the terminal it happens again. Also put metacity--replace in the terminal but still does the same in every startup. Tried to go to gconf-editor disabled composition manager for metacity. Compiz still appears under application in gconf . It is not under preferences and systems tools though. The other thing is that I can not choose from and options on visual effects. it is predetermined on none. Checked if video card was working and everything seems alright.

Does anyone know a solution?

---

### Post by blazemore on 2009-11-16
yes I have a solution.
While you're logged in, hit ctrl+alt+f3 to get to another display
Log in,
type sudo apt-get install fusion-icon
Hit ctrl + alt + f7 to get back to X
Hit ctrl + F2 to get the run dialogue,
type in fusion-icon, press Enter
Right-click on the new icon in the notification area,
from here you can select different options related to window managers etc.

---

### Post by juanmunoz on 2009-11-16
when I try to run fusion icon this error appears.

* Detected Session: gnome
 * Searching for installed applications...
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'

It appears under system tools but I try opening it and it does not load. :(

---

### Post by P4man on 2009-11-16
First make sure you have installed this package:
```
compizconfig-settings-manager
```

Through synaptic or by entering

```
sudo apt-get install compizconfig-settings-manager
```

in a terminal. Then you can configure compiz through system > preferences > compizconfig some long name.

Make sure you enable the plugin "window decoration"

---

### Post by juanmunoz on 2009-11-16
I will try this ,but I don't want compiz really . I want metacity to work on login. Because I have to load it manually and if it disables during session, I have to reboot and manually do it again.

---

### Post by blazemore on 2009-11-16
Well if all else fails you can just add metacity --replace to the list of startup items. (In the System menu)
First though, hit Ctrl + f2 and type it, to get it running for that session. if you do it in a terminal, it will disappear when you close it.

---

### Post by P4man on 2009-11-16
First of all, realize that the "desktop effects" **is** compiz (just a bare minimum of effects/plugins enabled). If that doesnt work, then neither will "installing compiz" (its already installed normally, just not enabled and without fancy GUI to configure it).

The other thing to realize is that by default compiz uses metacity to draw windows borders. You can install a different one, like emerald, but you dont need to (and you probably shouldnt)

Im not sure what package you tried installing but you probably messed it up somehow by installing the wrong one. Try this perhaps:

```
sudo apt-get install --reinstall metacity
```

---

### Post by juanmunoz on 2009-11-16
Thanks for the help it seems when I reinstalled metacity and installed fusion icon a least I can select between both. Compiz option never worked on changing station and mostly any effects. But I soleved the main problem

thank you for the help :)

---

