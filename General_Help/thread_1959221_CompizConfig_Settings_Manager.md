---
title: "CompizConfig Settings Manager"
date: 2012-04-15
forum: General Help
---

### Post by goaliedude3919 on 2012-04-15
I recently installed Ubuntu 11.10 on my laptop and just heard about CompizConfig Settings Manager so I downloaded it to hopefully make some settings more to my liking. After going through and editing multiple settings, none of the settings have saved or taken place. For example, I edit the settings to only have one desktop instead of the standard four in a 2x2 grid. All four desktops are still there. I also tried changing the Panel and Launcher Opacity for Unity, as well as changing the Launcher icon size. None of those changed anything. 

I'm hoping that one of you guys will be able to help me figure out what's going on. Thanks in advance for any answers you guys might have.

---

### Post by davidftechman on 2012-04-15
> **goaliedude3919 said:**
> I recently installed Ubuntu 11.10 on my laptop and just heard about CompizConfig Settings Manager so I downloaded it to hopefully make some settings more to my liking. After going through and editing multiple settings, none of the settings have saved or taken place. For example, I edit the settings to only have one desktop instead of the standard four in a 2x2 grid. All four desktops are still there. I also tried changing the Panel and Launcher Opacity for Unity, as well as changing the Launcher icon size. None of those changed anything. 

I'm hoping that one of you guys will be able to help me figure out what's going on. Thanks in advance for any answers you guys might have.
type this in the terminal

compiz --replace


if that doesnt work restart/logoff your computer.

---

### Post by goaliedude3919 on 2012-04-15
> **davidftechman said:**
> type this in the terminal

compiz --replace


if that doesnt work restart/logoff your computer.
I tried that and my screen started flashing and freaking out. None of the changes were made, but the following text came up in the Terminal:
```
jeff@jeff-Latitude-E6420:~$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
jeff@jeff-Latitude-E6420:~$ 
(metacity:31411): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:31411): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:31411): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:31411): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_group"
^C
jeff@jeff-Latitude-E6420:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4600012 (unity-2d-p)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x5a00004 (unity-2d-s)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c000e9 ([ubuntu] C)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

---

### Post by goaliedude3919 on 2012-04-16
I just tried both logging out and restarting my computer. Neither has had any effect on the changes taking.

---

### Post by stinkeye on 2012-04-16
What GFX driver are you using.
In the terminal...
```
sudo lshw -c video
```

Have you checked in **additional drivers** for a driver for your GFX card.
Search **additional drivers** in dash.


Is your GFX card capable of running unity with compiz
```
/usr/lib/nux/unity_support_test -p

```

Check you are logging into the **Ubuntu** session and not the **Ubuntu** 2d session.
[ATTACH]216096[/ATTACH]

If changes made in ccsm are not taking effect you're probably being dropped back to the 2d session.
What session am I in?
```
echo $DESKTOP_SESSION
```

---

### Post by goaliedude3919 on 2012-04-16
It would appear that my problems are stemming from my computer using Unity 2d. When I log in, the settings are on normal Unity, not Unity 2d. But when I run "echo $DESKTOP_SESSION" it comes back with Unity 2d. When I first installed Ubuntu, I know my computer was running normal Unity. After looking up some of the differences, one of the differences is Unity 2d has a less fancy window switcher (Alt+Tab). At the beginning, I had the fancier window changer, but after an update, that went away and I was always wondering what happened to it.

When I use the Additional Drivers app, it says "No proprietary drivers are used on this computer". However before that one update I know that there were options there. Is this a known bug? Is there anything I can do to get normal Unity back?

---

### Post by stinkeye on 2012-04-16
What is your output for
```
sudo lshw -c video
```
and
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by goaliedude3919 on 2012-04-16
> **stinkeye said:**
> What is your output for
```
sudo lshw -c video
```and
```
/usr/lib/nux/unity_support_test -p
```
Results for the first one:
```
  *-display               
       description: VGA compatible controller
       product: GF108 [Quadro NVS 4200M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e4000000-e4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:4000(size=128) memory:e5000000-e507ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:e5400000-e57fffff memory:c0000000-cfffffff ioport:5000(size=64)
```Results fro the second one: 
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```I would imagine that second one is the problem. Seeing everything saying "missing on display" doesn't seem good lol.

---

### Post by stinkeye on 2012-04-17
It appears to be a gfx card issue.
I'm not really familiar with the different issues.
May be the card using nvidia "optimus".
Did a quick search.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?p=11814196[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=11814196")

---

### Post by sojin on 2012-04-17
I can also confirm the same issue what 'goaliedude3919' mentioned above
When I installed Ubuntu 12.04 first time, I'm sure it was using Unity (echo $DESKTOP_SESSION returned unity at that time)

But after I upgraded my driver from default driver to Nvidia 295.40, it is falling to Unity-2d now.

sudo lshw -c video  returned:

  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:db000000-dbffffff memory:c0000000-c7ffffff memory:c8000000-c9ffffff ioport:d000(size=128) memory:dc000000-dc07ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:dc400000-dc7fffff memory:b0000000-bfffffff ioport:e000(size=64)

and

/usr/lib/nux/unity_support_test
Xlib:  extension "GLX" missing on display ":0".


Any help or clue ?

---

### Post by rajtendulkar on 2012-04-17
You could also give a try with Fusion-Icon - 

[HTML]
http://wiki.compiz.org/CompizFusionIcon
[/HTML]

it has option of reload window manager, which refreshes the settings.

---

### Post by stinkeye on 2012-04-17
> **rajtendulkar said:**
> You could also give a try with Fusion-Icon - 

[HTML]
http://wiki.compiz.org/CompizFusionIcon
[/HTML]

it has option of reload window manager, which refreshes the settings.

Fusion-icon is just an app to run commands to switch window managers/decorators or reload them.
Won't really help here.
I suggest you search for your card and compiz.

---

### Post by goaliedude3919 on 2012-05-23
Well I finally got this working. The answer was in one of those other topics that was linked, so thanks for that. What I ended up doing was disabling Optimus, which was a setting for the GPU built in to the Intel CPU. There was an option for it in the BIOS to toggle it off. It actually even says that Optimus isn't meant for OS's other than Windows. Thanks for all the help guys :)

---

