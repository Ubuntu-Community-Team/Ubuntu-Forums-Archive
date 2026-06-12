---
title: "Conky disappears after a while on 11.04"
date: 2011-05-24
forum: General Help
---

### Post by jespdj on 2011-05-24
Has anybody else noticed this problem?

When I run Conky on Ubuntu 11.04, then after some time it suddenly disappears (isn't drawn anymore on the desktop). With 'ps' I can see that the Conky process is still running, it just isn't drawing itself anymore.

I don't know what exactly triggers Conky to disappear. Does this have something to do with Unity?

---

### Post by TeoBigusGeekus on 2011-05-26
Kill it
```
killall conky
```
and start it from a terminal
```
conky
```
(or whatever)
to see if you get any error messages after it disappears.

---

### Post by TinEllus on 2012-05-24
This is happening to me too...

Conky starts at startup as conky -p 50 in Startup Applications

It disappears after a while, but conky is still running as seen in top.

It used to work ok, but started after "unity --reset" in terminal due to issues with windows focus.

After 'killall conky' and 'conky' in terminal it starts again, but disappears again after a few minutes.

No traces of anything doing anything to conky in .xsession-errors; I don't know what other logs to look for...

Please help

Precise Pangolin, Intel® Core™ i5-2430M CPU @ 2.40GHz × 4 , 64-bit, Kernel Linux 3.2.0-24-generic, Gnome 3.4.1, VESA Seymour video driver, AMD Radeon HD 7400

---

### Post by TinEllus on 2012-05-24
Sorry, seems to be an old and already solved problem

If it can help: conky is minimized by the Show Desktop button in launcher.

To solve the issue: start the Compiz configuration settings manager, go to "General Options" and uncheck the "Hide Skip Taskbar Windows" option.

Problem solved...

---

### Post by Frogs Hair on 2012-05-24
Thread solved ?

---

### Post by hollerith on 2013-01-16
No.  Clicking on the desktop in 13.04 makes conky disappear but is visible when the cube is rotated!

---

### Post by Frogs Hair on 2013-01-21
In the .conky rc you can try changing own_window line.

own_window yes
or
own_window conky
or
own_window desktop

---

### Post by stinkeye on 2013-01-21
```
own_window_type desktop
```
makes conky disappear when clicking the desktop.

Change to... 
```
own_window_type normal
```

and check you also have this setting...
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

If you start conky simply with the command "conky" you can open the config to edit with the terminal command...
```
gedit ~/.conkyrc
```

---

