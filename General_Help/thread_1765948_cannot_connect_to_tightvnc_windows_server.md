---
title: "cannot connect to tightvnc windows server"
date: 2011-05-23
forum: General Help
---

### Post by mons00n on 2011-05-23
Hi everyone,

I'm having an issue connecting to my media PC running windows 7 x64 using the remote desktop viewer built into my ubuntu 10.04 x64 install.  I *can* connect to the windows machine using chicken of the VNC on my mac with zero hassle.  Unfortunately when I try and use remote desktop viewer on my ubuntu destkop I get an immediate:

```
Connection to host 192.168.1.103 was closed.
```

I've tried connecting to 192.168.1.103::5900 as well, with the same result.  Again I **can** connect using my mac (using chicken of the vnc), just not remote desktop viewer =(  Any thoughts on why this might be?

Remote desktop viewer on my desktop has successfully connected to other Ubuntu & OSx machines...just not the tightvnc on my windows pc....

---

### Post by linuxinstalledfromhdd on 2011-05-23
Have you tried Teamviewer 6?

---

### Post by trozamon on 2011-05-23
Personally, I like RealVNC, which is open source and free for personal use. It's always worked for me. I've ran the server on a windows machine and accessed it from both ubuntu and my iPod Touch.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Teamviewer is free. If you want a licence or whatever, you would need to contact them, and I'm sure they would probably be happy to assist you with one.

---

### Post by trozamon on 2011-05-23
Sorry, not bashing TeamViewer (I actually like it quite a bit), but if he wants VNC, I was just recommending RealVNC.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I would truly recommend setting up NFS and share the folders just like you would on a file server, but that might be too primitive for what they are using it for too (i.e. media center)

---

### Post by mons00n on 2011-05-23
My goal was to simply VNC into the system and adjust system settings and what not so I didn't have to use a keyboard and mouse when those times arose.

It's just weird that remote desktop viewer isn't working in this instance

---

### Post by linuxinstalledfromhdd on 2011-05-23
Well did Teamviewer work? Maybe it is a port issue.  Maybe it's a windows security feature?

---

### Post by mons00n on 2011-05-23
> **linuxinstalledfromhdd said:**
> Well did Teamviewer work? Maybe it is a port issue.  Maybe it's a windows security feature?

Haven't had the chance to try anything else yet.  It just bothers me that it works from my mac and my desktop can connect to other VNC machines via remote desktop viewer.  It's really a minor issue at the moment was just hoping someone else had ran into it.  I'll give another VNC server a try in a bit and see if that helps.

---

### Post by linuxinstalledfromhdd on 2011-05-23
It sounds like a windows port issue, almost. Or a windows security feature. I'm not sure. 

If you want to set up a file server from the window shared folder to other systems (mac, linux, etc) I recommend setting up a NFS file server when it comes to stablity.

---

