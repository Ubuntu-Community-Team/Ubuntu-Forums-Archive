---
title: "Administrating a machine I can't get to..."
date: 2006-05-06
forum: General Help
---

### Post by Littleweseth on 2006-05-06
G'day folks;

I'm currently sitting on a Windows box trying to configure my Ubuntu server, which (for various reasons) is sitting in my friend's locked room at college. (Really frustrating, actually. It's maybe five or ten metres away from me right now, but it might as well be on the other side of the moon.)

Right now I find myself wanting to use the GUI configuration dialogs (i.e. Networking, Users or whatever user administration is called), but while I have sucessfully installed Cygwin/X I can't figure out the names to call these programs. I also tried starting a new gnome desktop service, but Ubuntu doesn't seem to want to spawn one on my Cygwin X Server over here because it's already running one locally.

My next call was to try installing VNC using synaptic : I tried firing up Synaptic and selecting the vnc4-common and vnc4server pacakges, but when I go to apply changes it asks me to insert the Ubuntu CD.. which is a tad challenging, seeing as I don't have a teleporter handy right now. Is there a way to force it to fetch the required packages from the repositories rather than a CD? I was thinking about editing the sources list, but I'm not precisely sure what to do.

Any help appreciated :D Cheers;
-lws

---

### Post by Ramses de Norre on 2006-05-06
You can comment out the first line, the one that starts with deb cd-rom or something like that.

---

### Post by Littleweseth on 2006-05-06
That was quite easy :p I just did it from Synaptic... silly me for not thinking of it.

My problem now progresses to getting VNC working. I start a vnc server using 'vncserver :1', then try to connect to it from windows using just the ip, but all I get is 'unable to connect to host : Connection refused (10061)'. The machine is definitely alive and at the IP address I specified. I've tried reading the relevant man pages (vncserver, vncviewer, vncconfig, xvnc) but couldn't extract any useful info from them. I also tried reverting to VNC Viewer 3.x on windows; same thing.

I also tried to start a listen server on my windows computer and then run 'vncconfig -display :1 -connect [ip-addr]', producing the following;
```
lws@Helios:~/.vnc$ vncserver
New 'Helios:1 (lws)' desktop is Helios:1

Starting applications specified in /home/lws/.vnc/xstartup
Log file is /home/lws/.vnc/Helios:1.log

lws@Helios:~/.vnc$ vncconfig -display :1 -connect 137.219.143.237
vncconfig: unable to open display ":1"
lws@Helios:~/.vnc$
```

This puzzles me slightly. One would expect to just start a vncserver and then connect to it with just an IP. 0.o

Using latest version of RealVNC for windows.

---

### Post by Tim Thumb on 2006-05-06
Is the machine definitely awake? If not VNC won't work. You would need to wake up the machine first. I use [this]("http://www.depicus.com/wake-on-lan/wake-on-lan-gui.aspx") to wake up machines from a Windows box. You'll need the MAC address of the machine. Then try your VNC software.

---

### Post by Littleweseth on 2006-05-06
The machine is very, definitely alive. It's serving webpages and I'm sshing into it just like normal. Pinky-promise :p

---

### Post by Littleweseth on 2006-05-06
Problem mostly resolved. I booted Ubuntu live and had a gander at what the stuff on the main menus actually pointed to, and noticed that all the config panel shortcuts were things starting with gnome-. A "locate gnome-" later, I had a very large list of things to sort through. Eventually I figured out that the action was all in /usr/bin, so I went there and found most of the things I was looking for. It's a tad cumbersome (and users-admin, the thing I was really looking for, didn't actually start with gnome-) but hey, it works.

I'd still like to get VNC working, though, just for the hell of it. My newly found 'locate binary I want with console commands, then run using Cygwin/X' method is quite fun (and an order of magnitude more snappy than VNC), but lacks elegance and friendliness. After all, using VNC is like sitting at the computer itself.. except the world is laggy and only in 65536 colors :p

EDIT : screw using locate, I just figured out you can actually open gnome-panel. gnome-panel + nautilus gives you both the panel and the desktop, w00t! [ This entire issue has been a great educational experience on how the Gnome Desktop + X-Windows actually works... silver linings and all, methinks :D ]

Cheers;
-lws

---

