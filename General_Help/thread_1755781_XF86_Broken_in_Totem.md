---
title: "XF86 Broken in Totem"
date: 2011-05-11
forum: General Help
---

### Post by shaveyourlife on 2011-05-11
When I first installed Ubuntu 10.04, my XF86 buttons worked perfectly with Totem.  I could pause, stop, fast forward, etc with no problems.  I would prefer to use VLC or something as my media player, but I could not figure out how to get these media buttons to work so I just stuck with Totem.

Well, within the last couple of weeks my XF86 buttons have run into some issues.  If Totem is in the foreground, they all still work perfectly, but if Totem is minimized or not the focus window the buttons no longer interact with it in any way.  My volume keys still control the system volume with no problems. If I am working in emacs and I press the play/pause button emacs will print the error "<XF86AudioPlay> is undefined".  So I know that the system is getting the commands, but they aren't being sent to the right windows.  Is this an X11 problem?  gstreamer? Any ideas?

---

### Post by no2498 on 2011-05-11
i just started seeing they are not loading all the gstreamer's they used to load

for gstreamer you need the good,bad,ugly, and 10 for the ubuntu/linux you use
you can find them in your package manager

---

### Post by shaveyourlife on 2011-05-11
I just checked, and I have all of those packages installed.  Any other ideas?

---

### Post by no2498 on 2011-05-12
i use sm player 

you may try setting the plug in in gstreamer-properties 

in a terminal type gstreamer-properties click enter

click video

set the plug in to x window system no xv

thats what i have

---

