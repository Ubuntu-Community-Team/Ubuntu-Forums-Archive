---
title: "Black box around Cairo Dock - Compiz"
date: 2011-10-23
forum: General Help
---

### Post by Cavsfan on 2011-10-23
Wondering if anyone would know why I now have a black box around my Cairo Dock. It just started happening a few days ago.
As you can see from the picture, it stays on top of everything. I have compiz along with Emerald and clicking on Reload Window Manager 
does nothing.
I have generic Lucid 10.04 LTS.

Cairo-Dock version 2.1.3-10-lucid-0ubuntu1 (Lucid)
Compiz version 1:0.8.4-0ubuntu15.3 (lucid updates)
                       1:0.8.4-0ubuntu15 (lucid)

It has been so long since I have messed with it I don't remember much about the settings but, other than the black box I cannot switch to Emerald.

I also just noticed that I cannot ALT+TAB between windows so it's like the windows manager is messed up.
I went through this before and tried uninstalling and re-installing and ended up doing a clean install to solve the problem.

I do not really want to do that again.

Thanks for anyone's help :)

[[IMG]http://ompldr.org/tYXh6Mw[/IMG]]("http://ompldr.org/vYXh6Mw")

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
the black box is due to compositing not being turned on.

if you have ccsm  (compiz config settings manager) use it to turn on compositing.

---

### Post by Copper Bezel on 2011-10-23
If both Alt+Tab and compositing are failing, that does point to a window manager problem. If you check your System Monitor, I think you'll find that Compiz isn't running at all; since your window title bars are present, you're probably running Metacity, which (prior to Gnome 3) doesn't composite by default like Compiz does. Compositing _[can be enabled in Metacity]("http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/")_ with a quick command, but you'll probably want to work out the Compiz problem instead.

Confirm that Compiz isn't running through the System Monitor, then try running 

```
setsid compiz --replace
```

in a terminal and reporting what errors are kicked back.

---

### Post by Cavsfan on 2011-10-24
I could not find compositing in ccsm.

I looked in System Monitor and compiz is not running. But, metacity is running. 
Here is the output:

```
cavsfan@cavsfan-desktop:~$ setsid compiz --replace
cavsfan@cavsfan-desktop:~$ compiz (core) - Fatal: No valid GL extensions string found.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
cavsfan@cavsfan-desktop:~$ Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
 
```I cannot even see Cairo-dock in the Applications menu any more. Although both are installed according to SPM.

Thanks!

---

### Post by Cavsfan on 2011-10-26
Still no go. I did find this out when I killed cairo-dock and started it back up in terminal:

```
cavsfan@cavsfan-desktop:~$ killall cairo-dock
cavsfan@cavsfan-desktop:~$ cairo-dock -o
warning :  (cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...
warning :  (cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:282)  
  GLX version too old (1.2).
Cairo-Dock needs at least GLX 1.3. Indirect rendering will be toggled on/off as a workaround.

 ============================================================================ 
    Cairo-Dock version: 2.1.3-10-lucid
    Compiled date:  Apr 22 2010 01:10:48
    Running with OpenGL: 1
 ============================================================================

```I looked in SPM and did not see GLX. It says I have 1.2 and it needs 1.3
I'm trying to keep this install generic LTS Lucid with the exception of the video driver.

---

### Post by Quackers on 2011-10-26
In a terminal run ```
compiz --replace
``` Are any errors reported?

---

### Post by Cavsfan on 2011-10-26
> **Quackers said:**
> In a terminal run ```
compiz --replace
``` Are any errors reported?


Yes, here it is. The screen went blank for a second when I entered that.

```
cavsfan@cavsfan-desktop:~$ compiz --replace
compiz (core) - Fatal: No valid GL extensions string found.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

Thanks Quackers!

---

### Post by Cavsfan on 2011-10-26
Sorry for bugging you all. I started to look into GLX and found that was involved with the video driver.
I installed the latest nvidia driver 285.05.09 and the problem is now fixed.

Thanks! :)

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-27
hurray!!

---

### Post by Cavsfan on 2011-11-03
Meant to say thanks to **Copper Bezel** and **Quackers** for providing the compiz commands.
I didn't know that compiz was not running nor did I know that there was a GLX error which led me to 
my video driver.
:popcorn:

Everything is looking great now.

---

