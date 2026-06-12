---
title: "Want to make a starup script"
date: 2009-10-06
forum: General Help
---

### Post by t4ggs on 2009-10-06
Hi, I want to make a startup script to close gnome-do and launch it again...
im having this bug [https://bugs.launchpad.net/do/+bug/290136](https://bugs.launchpad.net/do/+bug/290136)
and i want to solving by making this script, so how do i do it?? something like that?

> #! /bin/bash
kill gnome-do
sleep 5
gnome do


is that ok??? i dont really know... then i make it executable and run it at start up right????

---

### Post by stinkeye on 2009-10-06
> **t4ggs said:**
> Hi, I want to make a startup script to close gnome-do and launch it again...
im having this bug [https://bugs.launchpad.net/do/+bug/290136](https://bugs.launchpad.net/do/+bug/290136)
and i want to solving by making this script, so how do i do it?? something like that?




is that ok??? i dont really know... then i make it executable and run it at start up right????
You could just not use the Home shortcut and use your user name instead.
Enable the files and folder plugin and the shelf plugin.
Type in your user name in gnome-do and add it to your dock or add it to shelf.

---

### Post by VCoolio on 2009-10-06
As for the bug, in comment 48 there is a solution mentioned. Run
```
gksudo gedit /usr/share/applications/nautilus-home.desktop
```
And change the line starting with "Exec" to
```
Exec=nautilus --no-desktop .
```

As for the script:
1. the shebang (the first line) should not contain the space, so it should read #!/bin/bash
2. kill needs a pid to identify what to kill; you have the application name here so you'll need "killall gnome-do". 
3. You can instead of the sleep part use "killall gnome-do && gnome-do", the && means it will wait for the first command to finish and then execute the second (in which you made a typo btw, it's "gnome-do", not "gnome do").

---

### Post by t4ggs on 2009-10-06
Thanks to all of u


> **VCoolio said:**
> As for the bug, in comment 48 there is a solution mentioned. Run
```
gksudo gedit /usr/share/applications/nautilus-home.desktop
```
And change the line starting with "Exec" to
```
Exec=nautilus --no-desktop .
```



that would make the desktop my home folder...isnt it?

---

### Post by VCoolio on 2009-10-06
Yes, but you can make that whatever you want, just "nautilus --no-desktop ~/Desktop" for your Desktop or whatever.

---

### Post by t4ggs on 2009-10-06
> **VCoolio said:**
> Yes, but you can make that whatever you want, just "nautilus --no-desktop ~/Desktop" for your Desktop or whatever.

thanx

---

