---
title: "Making multible terminal command launcher"
date: 2010-01-13
forum: General Help
---

### Post by ArtzP on 2010-01-13
Little help is required!
I made gnome launchers (shortcut or what they are called). I selected them :** opened by terminal **(with some simple commands).  The problem is that I have 3 command lines and don't want to use 3 icons (launchers) to execute them. If I edit my launcer on gedit, I get this kind of lines :
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Icon[et_EE]=gnome-panel-launcher
_**Exec=xrandr -s 1024x768**_
Name[et_EE]=Arvutipilt 1: korda
Comment[et_EE]=Tavapilt
Name=Single desktop
Comment=Tavapilt
Icon=gnome-panel-launcher
```The problem is, when I put another command in the line, the commands won't work. I tryed ; and - mark between them, but no help.
I also tryed to make script, but it opens on gedit - not terminal.
Putting the **#!/bin/sh** to first line also won't help - it opens the script in wine (i don't know why).

Looking forvard to your help!

---

### Post by Is Mise on 2010-01-13
Try right-clicking on the script file and selecting Properties. Then go to the Permissions tab and check the "Allow executing file as program" box.

---

### Post by ArtzP on 2010-01-13
Thank you, 1 minute ago I realized it.
But is it possible to execute without notice and create it as launcher- multiplay commands?

---

### Post by Is Mise on 2010-01-13
If you drag the script file and drop it on the Gnome Panel, it can create a launcher for you.

---

### Post by stoneage on 2010-01-13
To execute consecutive commands try puttting them on a single line with && between each one.

It will execute each command in turn, but only if the previous one was successful.

---

### Post by ArtzP on 2010-01-13
Thank You for your answers. Next time I know :)

---

