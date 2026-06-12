---
title: "Gksudo/sudo for gui apps causes tightvnc to crash"
date: 2009-10-08
forum: General Help
---

### Post by CharlesA on 2009-10-08
I keep having this happen.

I ssh into my server, and start VNC to get to the desktop. I'll run something like gksudo gedit or sudo gedit. and VNC will terminate.

It doesn't happen all the time, but when it does, it's a pain in the butt, since I cannot kill the server on that display with vncserver -kill :display, and the PID isn't listed in ps aux.

Is there a way around this? I've been having to disconnect ssh and reconnect after forwarding another port so I can get back to a GUI.

If I run vncserver :60 after a crash, it says:

"Warning: thor:6- is taken because of /tmp/.X60-lock"
after removing that, it says: 
"Warning: thor:60 is taken because of /tmp/.X11-unix/X60"

After I remove that file, I am able to start up the server again.

I just want to know how to make it so that the server doesn't crash out when I try to run a graphical app with sudo. Command line works fine as far as I can tell.

Quite frustrating. :mad:

---

### Post by CharlesA on 2009-10-09
Haven't been able to find anything with google so far.

Any ideas?

---

### Post by CharlesA on 2009-10-15
Giving this one a bump. Still haven't been able to find any leads as to why this happens.

---

### Post by onurbiccud on 2011-03-05
I have exactly the same problem. Solved how? Thanks

---

### Post by twignation on 2011-07-19
Hello yes, I have the same problem, how was this solved?

---

### Post by allenbina on 2012-10-15
I'm also getting these issues.  

on a new vm, i'm installing gnome-desktop and tightvncserver.  It usually crashes within a minute of starting up.

---

