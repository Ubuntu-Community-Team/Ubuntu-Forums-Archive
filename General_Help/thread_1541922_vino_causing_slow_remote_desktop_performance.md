---
title: "vino causing slow remote desktop performance"
date: 2010-07-29
forum: General Help
---

### Post by captainentropy on 2010-07-29
Hi, I'm running Ubuntu Server 9.10. The machine is a server that I use for file storage and applications. It's probably obvious but I have to use a desktop viewer to access it for many things. I'm using VNC (Enterprise) as the client, though the problem I'm having I experience with TightVNC too. 
 
The Problem: When I access the desktop remotely it's very slow at redrawing the screen. If I access the server directly (with no one remotely connected) there is no such delay. Only when someone is connected to the server via remote desktop sharing does the sluggishness appear. 
 
So, vino is somehow causing the problem. The network connection is NOT the culprit. My building is gigabit throughout and it's currently reporting Line-speed = 20000 kbits/s. Another server in the same rack as mine does not have this problem. That machine is running CentOS and VNCserver.
 
What can I do? Is it easy to disable vino and install VNC?

---

### Post by captainentropy on 2010-08-02
disabling desktop effects (System>Preferences>Appearance>Visual Effects (tab) then select "None") made the performance better than before. But it's still slow compared to the CentOS machine using vnc4server.
 
To answer my own questions: yes, vino is easy to disable (just turn off remote desktop sharing), and NO vnc is NOT easy to setup. I'll try again some other time maybe. At least now it is usable and better with the desktop effects off.

---

