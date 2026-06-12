---
title: "ubuntu 10.10 - vnc with inetd only works for low resolutions"
date: 2011-02-06
forum: General Help
---

### Post by tails_naf on 2011-02-06
Hi All,

I have a real head scratcher here, that seems like a bug.

I was following this guide on how to setup multiple vnc desktops (i.e. seperate gnome-sessions, not the main one running on the machine)

[http://www.stuartellis.eu/articles/vnc-on-linux](http://www.stuartellis.eu/articles/vnc-on-linux)

And managed to get it more-or-less working.

The problem I have is, when I login to the desktop that is setup as 640x480, everything works fine*

If I login to the desktop that is setup as 800x600 (or higher), the ubuntu login screen that comes up seems to be 'hung', I can't click or type or login.

my .vnc/startup simply calls gnome-session

Any help to debug this would be greatly appreciated!!




* a few interesting things when it does 'work' - typing a 'd' on the vnc client (tried 2 separate clients) seems to minimise whatever window is active, other keys work as normal.

---

### Post by Rogach on 2011-08-18
I have exactly the same problem. Any suggestions?

---

