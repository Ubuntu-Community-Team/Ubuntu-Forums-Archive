---
title: "No more Window manager, no more 'minimize', 'maximize', 'close' button"
date: 2011-09-06
forum: General Help
---

### Post by Jimboland on 2011-09-06
I don't know what happend, but today I opened my computer and I couldn't see the taskbar anymore.
So  now the only way to close windows is via 'file', and select quit. And i  can't switch between windows anymore either, because there is no  taskbar. Even 'alt'+'tab' doesn't work!
When i try to open 'windows manager' in the control panel nothing appears, and all the other menu's open fine.
Can somebody help me with this really annoying problem?
XFCE Version - 4.8.0
Distro - Xubuntu 11.04
Slickness Black Theme

---

### Post by apmcd47 on 2011-09-06
If you have a terminal open, or a "run program" applet, type[PHP]xfwm4&[/PHP]into it. This should bring back the window manager.

Failing that what happens when you log out and in again?

Andrew

---

### Post by Jimboland on 2011-09-06
'Unable to locate theme engine in module_path: "ubuntulooks",'

when i try sudo + command i get:
'[1] 2419'

And when i reboot my machine nothing changes. 
If i want to login as root i can't either. I can use sudo, but i can't login as root:confused:

There are many strange things going on here, if i play a video, i can't maximize the screen..

edit: I just noticed that the 'non default xfce' programs can still be operated in a normal way. 
So the windows appears normal, i can close, minimize and maximize...

edit2: Its working again. apparently, when i open two NON standard XFCE proggrams, everything is normal again.
My taskbar is back and can use alt+tab again. Aslo, i can watch full screen video's again. AND the "minimize all open windows and show desktop" button is working again as well.
I didn't reboot yet, i'm affraid, now its working :) 
But anyway, this is a serious bug. I have to report it.

---

### Post by Jimboland on 2011-09-06
> **apmcd47 said:**
> If you have a terminal open, or a "run program" applet, type[PHP]xfwm4&[/PHP]into it. This should bring back the window manager.

Failing that what happens when you log out and in again?

Andrew

It happend again, and this time the command worked! Thanks!!:p
But each time I reboot, i have to type the command again. Is there a fix for this?

Thanks,

Jimmy

---

