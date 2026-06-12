---
title: "Tight VNC Server Not Working Correctly"
date: 2010-08-23
forum: General Help
---

### Post by snorkytheweasel on 2010-08-23
64-bit lucid lynx ***server*** (gnome)
According to Ubuntu Software Center, Tight VNC Server is installed. However,
[LIST=1]
[*]mlocate doesn't show any vnc files in any *bin directory
[*]ps -A doesn't show a vnc service running
[*]none of the menus have an item for vnc server
[/LIST]

I can connect to the ubuntu computer from Windows tightvnc clients on two different windows boxes. I can use the keyboard to type in the password. After that, remote control, i.e., the mouse, doesn't work.

The problem is that the mouse cursor (controlled from the windows client) moves but otherwise has no effect. I can move the cursor, but it acts as if the client (or server) is set to view-only. The effect of that is that I can't launch any programs (not even a terminal).

I've tried various combinations of settings on the client and on the server, but I can't get it to work correctly.

On the ubuntu machine, remote desktop sharing enabled.

Note: on some earlier versions of ubuntu this worked correctly when connecting from the same windows client using tightvnc.

I tried connecting from another windows client and got the same results.

Disclosure: This is a cross-post. I originally posted this in the "Networking" forum and got no responses.

---

### Post by keb329 on 2010-10-10
Did you ever find a solution to this issue?  I'm having the exact problem and can't seem to find a way to make the mouse work.

KB

---

### Post by perspectoff on 2010-10-10
Personally, I have found TightVNC server in Linux quirky.

I much prefer X11VNC Server.

The TightVNC clients (from Windows for example) can access the X11VNC server without any problem.

---

### Post by snorkytheweasel on 2011-02-24
> **keb329 said:**
> Did you ever find a solution to this issue?  I'm having the exact problem and can't seem to find a way to make the mouse work.

KB

No, unless reinstalling the OS counts as a solution.

---

