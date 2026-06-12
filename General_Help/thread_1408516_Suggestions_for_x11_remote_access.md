---
title: "Suggestions for x11 remote access"
date: 2010-02-16
forum: General Help
---

### Post by admkenshin on 2010-02-16
Hi everybody,

I am currently in need of remotely accessing an application on my home computer. It is a little too much for my poor netbook. Therefore, I have looked into various solutions for remote access, but I am not sure of which would be best in my case, so its time to ask the experts :D

The program in question is the Nios2IDE (its eclipse). I've found the following three options:

1. VNC. This is probably the easiest to set up, and it wont kill all your running processes if you're disconnected. Unless I use some sort of SSH tunneling though, its insecure, not to mention pretty boring to set up ;).

2. X11 over SSH. Now this sounds like fun to use, and I can bring just one app through, and not the entire desktop environment, which would save bandwidth.

3. Ubuntu-LTSP: I have no idea what this is (X11 forwarding?), but it definitely sounds interesting. This is something I could try just for the learning experience, but the little info I could find on the canonical site didn't tell me anything.

So, which one should I use?

Thank you for taking your time to read this,
admkenshin

---

### Post by bodhi.zazen on 2010-02-16
Use ssh -X

You may forward a single application or an entire desktop, you can forward the desktop to a new X session if you wish, either on a new tty (Ctrl-alt-F8) or Xephyr

For examples / ideas see :

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

If you like, forward gnome panel ;)

If you are connecting from a windows machine, use putty + Xming (Xming is an x server for Windows).

---

### Post by admkenshin on 2010-02-16
Ok, I will try that! I don't need an actual X server running on the app server right?

---

### Post by lukeiamyourfather on 2010-02-16
> **admkenshin said:**
> Ok, I will try that! I don't need an actual X server running on the app server right?

I don't think so, since its running the actual X session locally. If its an OpenGL application like CAD/CAM or 3D then it'll be using the local graphics card. VNC might be better in that case since it would be using the remote graphics card and sending bitmaps (so the local GPU doesn't have to be fast). Cheers!

---

### Post by bodhi.zazen on 2010-02-16
> **admkenshin said:**
> Ok, I will try that! I don't need an actual X server running on the app server right?

You do not need the X server on the server, no.

---

