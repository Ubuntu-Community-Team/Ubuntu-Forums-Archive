---
title: "Compiz water plugin"
date: 2006-06-08
forum: General Help
---

### Post by The_Tankengine on 2006-06-08
I have XGL all set up and running fine and stable.
The only problem is that I can't run the "water" plugin with compiz.
This error just pops up infinitely:
```
compiz.real: water: GL_ARB_fragment_program is missing
```
I am guessing i have to install it somehow, but I can't figure that part out.

Here is my "compiz-start" file in /usr/bin:
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &

```

Any help is greatly appreciated!
Thanks,
Thomas

---

### Post by jdusablon on 2006-06-09
I was going to say put water last in your compiz plugin load sequence, but you already seem to have that.

I've had many problems with these new plugins...mainly hardlocks. Had to disable many of them, including water. I kind of think water is pointless anyhow.

---

### Post by patrickfromspain on 2006-06-09
can't help with the pluggin. In my laptop, with AIGLX it doesn't work. In my desktop it works fine. Anyway, I have disabled it in both computers... it's nice, but it's totally useless.

---

### Post by Yohumbus on 2006-06-09
GL_ARB_fragment_program is an openGL extension that uses your graphics card for something. Unfortunatly this is functionality that your hardware is lacking so it can't be installed. You aren't really missing out though... If you can run all the other stuff then water isn't all that great.. plus it uses a ton of cpu power to run it (at least on my laptop it does)

---

### Post by angkor on 2006-06-09
[QUOTE=The_Tankengine]The only problem is that I can't run the "water" plugin with compiz.
[/QUOTE]

It could be your Nvidia Geforce4 GO doesn't support pixel shaders, if it does, read this thread, there are some people with the same problem.

[http://www.compiz.net/viewtopic.php?id=43&p=1](http://www.compiz.net/viewtopic.php?id=43&p=1)

---

### Post by Bokonon on 2006-06-09
Water is pretty much a waste.  I can't see how that can help your productivity.

It looks pretty cool until you get sick of it.  Save yourself the trouble and don't worry about it.  :p

---

### Post by anodizer on 2006-06-09
[QUOTE=jdusablon]I was going to say put water last in your compiz plugin load sequence, but you already seem to have that.

I've had many problems with these new plugins...mainly hardlocks. Had to disable many of them, including water. I kind of think water is pointless anyhow.[/QUOTE]


Hmm, could you be more specific? Which plugins did you disable and which vga do you use? Hardlocks are here too..:(

---

### Post by Half-Left on 2006-06-09
The water plugin requerers your card to support pixel shaders, Geforce3 and above support pixel shaders.

---

### Post by jdusablon on 2006-06-22
> Hmm, could you be more specific? Which plugins did you disable and which vga do you use? Hardlocks are here too..

Using gset-compiz or gconf-editor, I can't remember which, I disabled the following plugins:

**miniwin**
**dock** (I know what it does, just don't see the point, not as functional as taskbar. Cool, though)
**state**
**trailfocus**
**water** (what the heck! isn't this the oldest linux eyecandy in the world?)
**bs** (totally NOT useful)
**widget**
**gconf-dump** (not necessary unless troubleshooting)
**neg**

I'm not sure which one(s) were causing lockups, but I've been completely stable after disabling those.

---

### Post by zitch on 2006-06-22
**Dock** and **miniwin** were the only ones that were unstable for me.  Compiz kept crashing with either of those running.  But it never hard-locked on me; I was always able to recover by rerunning compiz.

I did have to do something for my ATI card to not hardlock.  It's one of the links in the main XGL/Compiz thread.

---

### Post by Anduu on 2006-06-22
The water plugin is known to be quite unstable...don't worry yourself over it.

---

### Post by jezjones on 2006-06-23
After my initial install on an intel 915 chip, I had water working well but at the cost of window decoration. Water was good when it rippled on error... like when you tab at a command line and there is no suggestions for text compleation.

Anyway, to make window decoration work i had to play with the order that they are listed in gconf-editor for loading. The compiz tool seemed to have little effect for me.
This may work for you, the water plugin definitely works on non-nvidia hardware.

---

