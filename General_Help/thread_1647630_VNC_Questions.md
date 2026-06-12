---
title: "VNC Questions"
date: 2010-12-17
forum: General Help
---

### Post by Caky on 2010-12-17
Hi,

I have some questions about VNCserver.

I want to setup a vncserver. But in this way:
- Starting the server by a command, like:

# vncserver --port=(port) --password=(password) --process=(proces id)

By process ID I mean, so I can attach it to a screen.
An exec command should be enough..

# --exec=`screen -x pid`

And what about if an user quits the screen ? Is there any way to quit VNC server then ?

Hope you guys can help me:P

---

### Post by Rocket2DMn on 2010-12-17
You can startup the VNC server in a screen instance if you want:
```
screen -S *foo* -d -m *bar*
```
where *foo* is the name of the screen session you can reattach to later:
```
screen -x *foo*
```
and *bar* is the command you want to run (e.g. vncserver ...)

You don't need to know the process id of screen or the vncserver. If the user is actually attached to the screen session, they can either detach from it or exit from it (the latter ends the session and thus shuts down the vnc server).

---

### Post by Caky on 2010-12-17
I have a server console running at a screen, so x11vnc needs to join that screen..

---

### Post by Rocket2DMn on 2010-12-17
I don't think I understand what you're asking in your last post. Please explain in more detail what you are trying to achieve.

---

### Post by Caky on 2010-12-18
Ok, I have a (game) server running in a screen..

So I want to let TightVNC (java console) connect to that screen, to see the server console..

I want to this trough using vncserver/x11vnc..


So if someone wants to see his server console, i'm making a VNC server..

Theory:
-> User clicks on "VNC Viewer".
-> Server creates a VNC server.
-> Server enters the server console screen.
-> User connects....
-> User can see the server console.

That's how it should be.:P

---

### Post by Rocket2DMn on 2010-12-18
What game are you running a server for? Is the server an Ubuntu Server install or something else?

Assuming this server console is a terminal and not a graphical interface, you don't need VNC at all - you just need a SSH server running on your game server and a SSH client on any remote box.  There are free clients available for Windows, too (like PuTTY). Once a user connects to the server over SSH, they can attach to the screen session that the server is running in.

In order to run vncserver, you will need a desktop environment installed on the server, which it may not have by default.  If you were to set this up, a user would still need to login to the server over SSH to create the vncserver, unless you set it up so that a vncserver is always running in the background.  Running vncserver is extra overhead that it sounds like you don't need.

---

### Post by CharlesA on 2010-12-18
Moved to *General Help.*

---

### Post by dwhitney67 on 2010-12-18
> **Rocket2DMn said:**
> 
In order to run vncserver, you will need a desktop environment installed on the server, which it may not have by default.  If you were to set this up, a user would still need to login to the server over SSH to create the vncserver...

This is exactly what I do; I run the following script remotely using SSH when I want to start up the VNC Server:
```

#!/bin/bash

vncserver :$1 -nohttpd -DisconnectClients=0 -NeverShared -localhost -depth 24 -geometry $2

```
The $1 arg is the display number, and $2 is the desired geometry (eg. 1400x900).

Once the script has been invoked, and a few moments have passed, then I can use my VNC client app to connect to the server (which btw, also uses SSH).

When I am done, I merely terminate the VNC client; the VNC Server continues running on the remoter server machine.

To terminate the VNC Server, I use a script on my client side to terminate the Server by using the display number.  This script is on my other computer (Mac), so I don't have access to it right now.  Btw, I rarely ever terminate the VNC Server.

---

