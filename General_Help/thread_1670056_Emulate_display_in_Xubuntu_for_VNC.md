---
title: "Emulate display in Xubuntu for VNC"
date: 2011-01-18
forum: General Help
---

### Post by jim2013 on 2011-01-18
I have a Xubuntu box that I use as a server (Apache2, FTP, etc.) that I have used xfce to set up. I currently have the box in a headless setup. I access the box both by SSH and VNC. When I boot the box with a display plugged in, Xubuntu automaticly logs in as my main account and boots properly. When I do not have a display hooked up on startup, the box auto logs in, but fails to start an X session. What I would like to do is to start a X session on system startup automatically. I have seen a tutorial on how to fool X into thinking there is a display attached by modifying xorg.conf, but the tutorial doesn't work for me. I need to be able to VNC into a full xfce session and have the session be persistent. I want to be able to have the server emulate a display so that X is started on that display. I then want to be able to VNC into that display for a persistent VNC session. I have seen this done as an example but I cannot figure out how to do it. 
Thanks,
Jim2013

---

### Post by theDaveTheRave on 2011-01-18
It's certainly possible to log into a specific display with VNC.

it's a while since I've done it, so this is from memory....

When you log in via SSH you then start your VNC server, and it returns the 'value' of your session.

You then need this as part of the login for your VNC viewer. If you fail to stop this particular VNC session the number will increment with each new connection (even if it is the same user).

So I assume that if you know the 'number' of the session you should be able to log into the same one again and again...??

I'll try to hunt down the help file I created for my colleagues, but as yet I haven't found it - I probably put it into their local wiki and stupidly failed to keep a copy for myself.

I don't know if it helps, but I have moved over to using freeNX, I don't know if this has the functionality you are looking for, but I personally find it much easier to use compared to VNC (especially as it has SSH tagged onto it automatically - so no need to create a tunnel as it is done for you).

David

---

### Post by jim2013 on 2011-01-18
When I boot without a display, I cannot seem to make Xubuntu think it has a display to open.I have tried with multiple VNC servers and clients. It simply refuses to open a session because there is not one already open.

Example errors from x11vnc

18/01/2011 15:59:48 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 1828
18/01/2011 15:59:48 XOpenDisplay("") failed.
18/01/2011 15:59:48 Trying again with XAUTHLOCALHOSTNAME=localhost ...
18/01/2011 15:59:48 
18/01/2011 15:59:48 *** XOpenDisplay failed. No -display or DISPLAY.

---

### Post by theDaveTheRave on 2011-01-18
not sure if this helps but I'll tell you how I did it when I used vnc.

___
The server (headless) wasn't always turned on. So I used 'wake on lan' to boot it up.

SSH into the box with my user account details.

Start the vnc server, make a 'mental note' of the display (normally starts at 0).

Open my vnc viewer and tell it to atatch itself to display zero.
___

Now as far as I am aware I could have stopped my SSH session and still loged into the vnc-server (using the correct display value during the connection). It was neccessary to kill each vnc-server process (and hence each display) separately.

Quick note.

Starting the VNC server this way is potentially unsafe, and it leaves a window open into the system. However if you set up the server to only accept 1 connection at a time it isn't so bad. BUT the info sent to the server is not encrypted (as far as I am aware). With freeNX it is (via SSH)but I'm not sure that FreeNX will give a persistent display that you can log into and out of as you please.

David

---

