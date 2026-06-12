---
title: "Wierd Xwindow problem 10.10"
date: 2011-06-09
forum: General Help
---

### Post by meburke on 2011-06-09
I've been having problems with my nVidia Ge9800 ever since I upgraded from 10.4.

I finally just uninstalled the nVidia card, ran X -configure and copied the resulting xorg.conf.new file to my xorg.conf.

Ubuntu still doesn't start X on boot, it drops me into the terminal.

If I run startx as root I get a new Gnome desktop. If I run startx as myself, I get a blank, dark screen with no mouse pointers or anything.

What I would like, is for X to start on boot and to load my old desktop.

Any suggestions?

---

### Post by TeoBigusGeekus on 2011-06-09
Delete your xorg.conf file and try booting without it.

---

### Post by meburke on 2011-06-09
Wow! That may be the strangest fix ever! It worked, and only after reading something aI saw on the 'Net did I realize that Xorg can do an autoconfig on the fly.

Thank you for your help.

---

### Post by TeoBigusGeekus on 2011-06-09
You're welcome.
Don't forget to mark the thread as solved.

---

### Post by meburke on 2011-06-13
I'm baaaack....

So, it worked once, but I rebooted and now I'm back to where I was, only now I don't have a conf file to delete...

There must be an explanation somewhere. I've had to stop working on the project I'm on to mess with this XWindows stuff. I'm trying to practice patience, and I'm willing to wade through a good tutorial or book on XWindows administration, but I can't seem to find one that makes sense.

Any suggestions, especially one as cool as the last one, would be very helpful.

Thanks,
Mike

---

### Post by meburke on 2011-06-13
I ran > dpkg-reconfigure xserver-xorg and that seemed to have no effect at all.

I ran > Xorg -configure. When I tested the xorg.conf.new I eventually got the "X" cursor on my screen. This is an improvement, since before it was simply a blank screen. At least I have some type of xterminal running.

> Startx from root gives me a good desktop. Unfortunately, it is not MY user desktop and I don't have the same configuration and tools.

So, I decided to start an xterminal session and see what happened. I ran > startx /usr/bin/xterm -- :1 from root and got a fully-functional xterminal. I tested xeyes and evolution and they worked fine...as root. When I did the same thing as me (default user meburke) I got a blank screen again. The F1 console showed a constant stream of "No protocol specified" messages. When I killed the process, I got the message, "xinit: resource temporarily unavailable (errno 11): unable to connect to X server".

So, at least it seems the problem is related to my default login and not the whole system, except, of course, I start up in a terminal instead of the gdm xwindows login prompt.

I think the way I would like to solve this is to get XWindows running properly for my default user, then fix the problem of not booting up into XWindows.

Does anyone have any suggestions for straightening this out?

Thanks,

Mike

---

### Post by meburke on 2011-06-13
Well, I had the xterminal running and ran gdm, and I got the login screen to log in as me again. This in turn gave me my default desktop and I can at least get back to work.

I would still like to find out how to fix this problem, but it looks like a person could make a career out of learning the XWindows system and I don't even know really where to start.

Any help or suggestions would still be appreciated.

Thanks,

Mike

---

