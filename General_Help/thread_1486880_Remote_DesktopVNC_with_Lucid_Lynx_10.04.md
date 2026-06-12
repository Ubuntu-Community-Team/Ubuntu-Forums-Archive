---
title: "Remote Desktop/VNC with Lucid Lynx 10.04"
date: 2010-05-18
forum: General Help
---

### Post by ksaul on 2010-05-18
My work computer and my home computer both have Lucid Lynx (10.04) installed. I have installed x11vnc, openssh, and vnc4server on my home computer and configured my router correctly. I can connect to my home computer and it prompts me for a password. I enter the password and am authorized but TightVNC viewer just shows a black screen. I tired connecting on my home network with Windows 7 & PuTTy and the same thing, just a blank screen. I can move the mouse on the VNC viewer, and it will move the mouse on the VNC Server, but there is no background, icons, or anything just a blank screen.

What am I doing wrong? I have been trying to setup remote desktop/vnc between my work and home computer for 2weeks now :mad:

---

### Post by cdenley on 2010-05-18
You have to configure VNC to tell it what to start.
[https://help.ubuntu.com/community/VNC/Servers#Customising%20your%20session](https://help.ubuntu.com/community/VNC/Servers#Customising%20your%20session)

For x11vnc, if you can't see your session, try enabling/disabling visual effects.
System>Preferences>Appearance

Or you can just use gnome's builtin VNC server, but you have to be logged in locally first.
System>Preferences>Remote Desktop

---

### Post by ksaul on 2010-05-18
[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

Bottom of the page is the answer, to get a full desktop, but my mouse clicks and keyboard wont work in the vncdesktop. The mouse moves on the screen but clicks are being registered

---

### Post by ksaul on 2010-05-18
> **ksaul said:**
> [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

Bottom of the page is the answer, to get a full desktop, but my mouse clicks and keyboard wont work in the vncdesktop. The mouse moves on the screen but clicks are being registered

:popcorn:

---

### Post by rabidfruitbat on 2010-05-26
I have my ubuntu 10.04 system automaticlly log me in.  I've set up sharing my desktop and I just get a black screen when using VNC in Windows, TightVNC in Windows and Remote Desktop Viewer under Ubuntu.  

When I first set up the system and logged in manually, I could use VNC to connect.  I then modified the system to automatically log me in when it reboots (so I could do remote reboots and still get access to the desktop).  Now I have the above behavior.

Where too from here?

---

### Post by fradicalone on 2010-05-31
I have the same problem. I notice every time I start a new VNC login on 10.04, in the Gnome Remote Desktop settings, the "You must confirm each access to this machine" is always reset. 

If I keep a VNC session active after setting this flag it works for a long time, but accidentally terminate VNC, then I need to take another trip to that PC to reset the flag. 

Is there anyway on Gnome Remote Desktop to disable this "feature". It kind of defeats the whole reason for remote desktop ...

---

### Post by deroby on 2010-08-03
Same here, I need to type the password on the *slave* machine before it can be taken over... kind of annoying as it has no monitor, mouse or keyboard attached normally ... :(

Update : as found in another thread : 

It's a bug. See:

[https://bugs.launchpad.net/ubuntu/+s...no/+bug/562423](https://bugs.launchpad.net/ubuntu/+s...no/+bug/562423)

There is a workaround in reply #11 in the thread. (Base64 encoding
of the password that is mentioned therein can be done with the "base64"
command, see "man base64" for details.)

---

### Post by DoritosBR on 2010-09-15
My problem was:
When I connected remotely on Ubuntu, after entering the password and successfully connect, it would just appear an black screen.

Turns out it was the compiz interfering with vnc.

I found this thread
[http://ubuntuforums.org/showthread.php?t=1496368](http://ubuntuforums.org/showthread.php?t=1496368)

1) Open a terminal o press ALT+F2, then run/type: gconf-editor

2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

And problem solved.

---

