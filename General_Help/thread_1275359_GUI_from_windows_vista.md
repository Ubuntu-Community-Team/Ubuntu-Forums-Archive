---
title: "GUI from windows vista"
date: 2009-09-25
forum: General Help
---

### Post by sri1116 on 2009-09-25
i am trying to connect to Ubantu linux from vista and install software in GUI mode using Putty.>I tried something like export DISPLAY=ipaddres:0.0
But this gives me error like """Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment""" Looks like package are installed on ubantu since I can open GUI mode from MAC os but not from vista
 
Please help me.
:confused:

---

### Post by blueridgedog on 2009-09-25
> **sri1116 said:**
> i am trying to connect to Ubantu linux from vista and install software in GUI mode using Putty.>I tried something like export DISPLAY=ipaddres:0.0
But this gives me error like """Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment""" Looks like package are installed on ubantu since I can open GUI mode from MAC os but not from vista
 
Please help me.
:confused:

You can't export a display to a vista (or any MS) system unless the vista system is running an X server, such as the windows version of exceed from hummingbird.

---

### Post by VipX1 on 2009-09-25
I have it working but on XP. I can run things like gedit and synaptic on the XP desktop via a ssh connection to my Ubuntu machine. I start Cygwin and then run Xwin server on Cygwin. Then I connect to Ubuntu via ssh using the Xwin server GUI. It is at this stage that typing sudo synaptic opens the synaptic GUI on XP.
In my experience most app's that work in XP also work on Vista.

Cygwin gives the effect of a Linux kernal running on top of windows XP. It's a brilliant little operating system when you really start using it. When you get it all working you can refine it as much as you like.

---

### Post by blueridgedog on 2009-09-25
Xwin server on windows is another working windows x server and should work like the exceed product.

---

### Post by RealG187 on 2009-09-25
I tried KDE for Windows but Krita is experimental and apparretnly WILL crash. Not could crash or has a good chance of crashing, but WILL as in it will for sure...

That's what I read.

---

