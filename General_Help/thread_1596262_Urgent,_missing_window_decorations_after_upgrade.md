---
title: "Urgent, missing window decorations after upgrade"
date: 2010-10-14
forum: General Help
---

### Post by turgidtoupee on 2010-10-14
I recently upgraded to 10.10 from 10.04, and after a few days I am now without window decorations for some reason. Whenever I launch a program from the panel or menu, it starts in the top left of the screen at some default-ish size with no window borders. alt-F4 doesn't work, and neither does alt-F2. None of the shortcuts defined by compiz work either. If I run compiz from terminal, all the windows and panels disappear for a few seconds, then reappear exactly the same.

---

### Post by turgidtoupee on 2010-10-14
Update, I switched to metacity and window borders are back. I'm without compiz however.

---

### Post by hawthornso23 on 2010-10-14
Try just switching back to compiz. The mere process of switching (in either direction) will often get windows decorations going again.

I had a problem with sporadic missing window decorations a while back. I went through my compiz settings and unselected some stuff that I didn't really need (for example I had the goldfish selected with an opaque cube) and that seems to have cured the problem.

---

### Post by turgidtoupee on 2010-10-14
> **hawthornso23 said:**
> Try just switching back to compiz. The mere process of switching (in either direction) will often get windows decorations going again.

I had a problem with sporadic missing window decorations a while back. I went through my compiz settings and unselected some stuff that I didn't really need (for example I had the goldfish selected with an opaque cube) and that seems to have cured the problem.

Tried that, nothing but the same.

---

### Post by yetiman64 on 2010-10-14
I too have been putting up with the windows decorations going missing occasionally, for quite a while now. I have gotten around it by installing fusion-icon & ccsm and putting a fusion-icon entry in startup applications so it is always running when the machine is on.

Note, I set the GTK window decorator option on fusion-icon (located in the notification area when running) as well as tick the windows decorations plugin in compizconfig settings manager.

Whenever the decorations disappear, it is very simple to right click fusion icon in the notification area and use Reload Window Manager, this brings back the decorations every time for me. 

This is not a fix by any means, more an easy (two click) workaround for my convenience.

---

### Post by sepo on 2010-10-14
I think it's a known bug..it also happents to me (10.04). I found this info on a forum:
[http://www.linuxforums.org/forum/ubuntu-linux/169134-emerald-fails-load-sometimes.html](http://www.linuxforums.org/forum/ubuntu-linux/169134-emerald-fails-load-sometimes.html)

I made two scripts on my desktop (you can also made them as launchers) to help me to resolve the issue with just two clicks (and without installing any app :)

the first: 
nohup gtk-window-decorator --replace>/dev/null &

the second:
nohup emerald --replace>/dev/null &

---

### Post by turgidtoupee on 2010-10-14
> **sepo said:**
> I think it's a known bug..it also happents to me (10.04). I found this info on a forum:
[http://www.linuxforums.org/forum/ubuntu-linux/169134-emerald-fails-load-sometimes.html](http://www.linuxforums.org/forum/ubuntu-linux/169134-emerald-fails-load-sometimes.html)

I made two scripts on my desktop (you can also made them as launchers) to help me to resolve the issue with just two clicks (and without installing any app :)

the first: 
nohup gtk-window-decorator --replace>/dev/null &

the second:
nohup emerald --replace>/dev/null &

I'm not using emerald. I tried completely removing all the compiz packages and installing again, but it did nothing.

---

### Post by fermulator on 2011-01-08
I've having the same problem, posting in #compiz in freenode, but no response yet.

Prior to the upgrade from Ubuntu 10.04 to 10.10, things worked fine.  Since the upgrade, when I run compiz, window decorations do not show up and are missing.  Running metacity shows the decorations...

> fermulator@fermmy:/etc/apt/sources.list.d$ dpkg --list | grep compiz
ii  compiz                                1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager
ii  compiz-core                           1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager
ii  compiz-dev                            1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager - development files
ii  compiz-fusion-plugins-extra           0.8.6-0ubuntu1                                    Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main            0.8.6-0ubuntu2                                    Compiz Fusion plugins - main collection
ii  compiz-gnome                          1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                        1:0.8.6-0ubuntu9.1                                OpenGL window and compositing manager - plugins
ii  compizconfig-backend-gconf            0.8.4-1ubuntu5                                    Compiz Fusion configuration system - gconf backend
ii  compizconfig-settings-manager         0.8.2-0ubuntu1                                    Compiz configuration settings manager
ii  emerald                               0.7.2-0ubuntu6                                    Decorator for compiz-fusion
ii  libcompizconfig0                      0.8.4-0ubuntu3                                    Settings library for plugins - OpenCompositing Project
ii  libcompizconfig0-dev                  0.8.4-0ubuntu3                                    Development file for plugin settings - OpenCompositing Project
ii  libemeraldengine0                     0.7.2-0ubuntu6                                    Decoration engines for compiz-fusion
ii  python-compizconfig                   0.8.4-2ubuntu2                                    Compizconfig bindings for python


I've tried: 
 1) ALT+F2: compiz --replace (flutters the screen as usual and reloads stuff, but doesn't fix)
 2) ALT+F2: metacity --replace (replaces with metacity, and window borders return, yay, but I want compiz...)
 3) ALT+F2: compiz --replace (replaces with compiz, window borders/decorations go away.. sad face)
 4) ALT+F2: "/usr/bin/compiz-decorator --replace" (nothing)
 5) ALT+F2: "/usr/bin/gtk-window-decorator --replace" (nothing)
 6) installed "emerald" and "fusion-icon" and fiddled with both ... to no avail.

... not sure what else to try ...

---

### Post by fermulator on 2011-01-08
After about an hour working with _coz and adamk in the compiz IRC channel, we finally figured it out!  I have an ATI Radeon card, and was running the open source Radeon driver (shouldn't be an issue).  But, the "reflection" plugin was enabled, and apparently there is a bug in the driver that the reflection plugin is trying to call ...

Disabling the "Reflection" plugin solved the problem, borders appeared.

---

