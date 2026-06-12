---
title: "Dont know how messed up my VNC setup is, help.."
date: 2012-05-02
forum: General Help
---

### Post by mYrN on 2012-05-02
Hello!

I have SSH access to my Ubuntu 10.04.4, and I would like to setup a VNC connection to it. The problem is that I cant use ports 590*. I have installed tightvnc server but it doesnt seem to work and Im not really sure what Im doing.. :( How can I setup the VNC server so that it listens to another port? I have port 52004 open, i need to use that for the VNC server.. I've googled like crazy but i cant find Anything on how to achive this :( Thanks so much in advance..!

---

### Post by steeldriver on 2012-05-02
you should be able to do it via ssh tunneling - no need to mess with any other ports since you already have ssh access (plus it will be secure)

there are lots of guides on line - try googling for one that's appropriate for your particular combination of ssh and vnc client/server

if you still want to change the port you could try x11vnc with the -rfbport option (or maybe tightvnc also supports -rfbport)

---

### Post by mYrN on 2012-05-02
Thank you, the rfbport worked!

---

