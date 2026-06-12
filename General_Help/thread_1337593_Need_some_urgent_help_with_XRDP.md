---
title: "Need some urgent help with XRDP"
date: 2009-11-25
forum: General Help
---

### Post by ZarathustraDK on 2009-11-25
So I'm doing this Linux-project for my company, and I've hit a bit of a snag with XRDP.

The problem is that we're using Dameware Mini-Remote-Control to remote to our pc's in connection with online support. Dameware can use 2 protocols for remotly accessing a desktop, a proprietary one and RDP. We can also use Windows Terminal Services if need be (RDP).

Now, I'm in the process of making a linux-image we can roll out on our customer pc's, but I can't for the life of me get XRDP to work the way I want it to. With the default setup I can remote to another machine, but it starts a new session which is not what I want. I want to be able to remote to the currently running session, as in "see what the customer is seeing". I know it can be done, but well, I fail to see how to fix it :-/

And no, direct VNC'ing to the computer is not allowed, as it that would entail installing a separate program just for that on all the support-pc's (yes it's a big deal ;) ), since XP does not have a VNC-client built in. Only Dameware or the remote desktop program that comes as standard with XP.

Any ideas?

---

### Post by abuster on 2009-11-30
This hack may solve your problem:

[http://ubuntuforums.org/showthread.php?t=392184](http://ubuntuforums.org/showthread.php?t=392184)

It describes how to start an session connecting to display :0.

> 
3) GNOME

Now comes messy but necessary part if you really want gnome.

To explain:
XRDP uses a file called startwm.sh to determine which Desktop environment to use. Any program can be run in this file (the defaults are things like gnome-session, but gnome session can't run inside Xvnc).

The only solution I can find is to first run x11vnc, which runs a vnc server that captures an already running session (hence the need to be logged in already) and then run vncviewer in fullscreen mode instead of having a desktop environment running.

so, backup startwm.sh
 	Code:
 	cd /usr/local/xrdp/
sudo mv startwm.sh startwm.sh.bak
sudo gedit startwm.sh 
and enter the following code into the file:
 	Code:
 	#!/bin/bash
x11vnc -display :0 -localhost &
sleep 5
vncviewer localhost:0 -fullscreen 
and make it executable:
 	Code:
 	sudo chmod +x startwm.sh 
Now, make sure you are logged on to your desktop, go to a windows machine and log onto you ubuntu machine using remote desktop, and hopefully it'll work.


Good luck;)

---

### Post by tonyurso on 2009-12-03
Thanks, Ive sent two days with a simular problem.

---

