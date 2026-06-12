---
title: "Cairo Dock not starting with Ubuntu 11.10"
date: 2011-10-25
forum: General Help
---

### Post by mderksen on 2011-10-25
Hello guys,

I tried to install Cairo Dock with Ubuntu 11.10 (64 bit) but it won't launch. I'm a bit new to Ubuntu but this is what i did.

I used this tutorial:
[http://www.noobslab.com/2011/10/cairo-dock-240-is-released.html](http://www.noobslab.com/2011/10/cairo-dock-240-is-released.html)

I opened the terminal:
```
sudo add-apt-repository ppa:cairo-dock-team/ppa
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```Cairo Dock is installed but when i try to start Glx-Dock it doesn't start. Nothing happens.

I use the Asus N53SV laptop with Nvidia graphics card. It uses the default Nvidia drivers Ubuntu selected.

Is there something i can check to get this working? 
Thanks in advance.

---

### Post by mderksen on 2011-10-26
[FONT=Arial]I probably know why it's not working. It's because of my videocard drivers but i don't know how i can install them right.

I looked at my opengl and it says:
```
**user@user-N53SV:~$ glxinfo|more**
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
name of display: :0.0
```I installed the Nvidia drivers with these commands:

[/FONT]```
[FONT=Arial]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-settings [/FONT]
```[FONT=Arial]

After a restart nothing is changed and also there is no xorg.conf file. So i created one with the command

```
sudo Xorg -configure
```After a restart Ubuntu won't start normal in graphics interface but i can enter code when i use CTRL + ALT + F2. When i rename the xorg.conf fille and restart Ubuntu start normal again.

Does anyone know how to install the nvidia drivers with opengl properly?
Thanks in advance
[/FONT]

---

### Post by Elmer Fudd on 2011-10-28
FYI.

Cairo dock worked for me for a while. Then one time I tried to start a Cairo (Gome with or without effects) session and I get a screen with my wall paper and the desktop management menu across the top but no Cairo-Dock. All three Gmome type sessions work fine as well as the 2 Unity session options.

I opened a terminal window and tried to start the Dock.
Got this:

> S1110:~$ cairo-dock

(cairo-dock:4455): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4455): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4455): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4455): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

 ============================================================================ 
	Cairo-Dock version: 2.4.0~2
	Compiled date:  Oct 11 2011 11:25:50
	Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)  
  Cairo-Dock has crashed (sig 8 ).
It will be restarted now.
Feel free to report this bug on glx-dock.org to help improving the dock!
info on the system :
Linux S1110 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
The applet 'stack' may be the culpritrestarting with 'cairo-dock -x "stack" -w 2 -q 1'...

(cairo-dock:4464): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4464): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4464): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4464): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

 ============================================================================ 
	Cairo-Dock version: 2.4.0~2
	Compiled date:  Oct 11 2011 11:25:50
	Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)  
  Cairo-Dock has crashed (sig 8 ).
It will be restarted now.
Feel free to report this bug on glx-dock.org to help improving the dock!
info on the system :
Linux S1110 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
The applet 'stack' may be the culpritrestarting with 'cairo-dock -x "stack" -w 2 -q 2'...

(cairo-dock:4473): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4473): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4473): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4473): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

 ============================================================================ 
	Cairo-Dock version: 2.4.0~2
	Compiled date:  Oct 11 2011 11:25:50
	Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)  
  Cairo-Dock has crashed (sig 8 ).
It will be restarted now.
Feel free to report this bug on glx-dock.org to help improving the dock!
info on the system :
Linux S1110 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
The applet 'stack' may be the culpritrestarting with 'cairo-dock -x "stack" -q 3'...

(cairo-dock:4482): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4482): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4482): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(cairo-dock:4482): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

 ============================================================================ 
	Cairo-Dock version: 2.4.0~2
	Compiled date:  Oct 11 2011 11:25:50
	Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)  
  Cairo-Dock has crashed (sig 8 ).
It will be restarted now.
Feel free to report this bug on glx-dock.org to help improving the dock!
info on the system :
Linux S1110 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux
The applet 'stack' may be the culpritrestarting with 'cairo-dock -x "stack" -q 4'...
Sorry, Cairo-Dock has encoutered some problems, and will quit.

---

### Post by Bobhuber on 2011-10-28
> **mderksen said:**
> Hello guys,

I tried to install Cairo Dock with Ubuntu 11.10 (64 bit) but it won't launch. I'm a bit new to Ubuntu but this is what i did.

I used this tutorial:
[http://www.noobslab.com/2011/10/cairo-dock-240-is-released.html](http://www.noobslab.com/2011/10/cairo-dock-240-is-released.html)

I opened the terminal:
```
sudo add-apt-repository ppa:cairo-dock-team/ppa
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```Cairo Dock is installed but when i try to start Glx-Dock it doesn't start. Nothing happens.

I use the Asus N53SV laptop with Nvidia graphics card. It uses the default Nvidia drivers Ubuntu selected.

Is there something i can check to get this working? 
Thanks in advance.
cairo-dock -o      to run with open GL and you shouldn't have to do anything with the standard nvidia drivers if your running the 3D version of 11.10

Mark this as solved if you have already figured this out.

---

### Post by mderksen on 2012-04-27
Late reaction but i solved it by installing ironhide ppa.

---

