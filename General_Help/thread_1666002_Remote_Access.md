---
title: "Remote Access"
date: 2011-01-13
forum: General Help
---

### Post by gliff159 on 2011-01-13
I have a Ubuntu 'server' as in it sits in my basement and i put files on it. Problem is that when I reboot it, not that it needs it often, it wont let me VNC in until I plug in a monitor and type in my password. It will let me log in thru ssh tho.

---

### Post by Azdour on 2011-01-13
Hi,

I also recently came across this same issue. The only solution I found so far was to install vnc4server.

Then when I ssh in I run vncserver. The first time you start it up (for that user):

 1. It will ask for the password to use
 2. It will start the vncserver and create a .vnc directory in your home dir.
 3. Then you need to kill the vncserver because it creates an incorrect xstartup file. To kill it you will probably run:
```
vncserver -kill :<display n>
```
Where <n> is the display number you see when it starts vncserver, e.g. :1
 4. Go into the .vnc directory, edit the xstartup file
 5. Change the last line to:
```
gnome-session &
```
 6. Save the file and restart vncserver

Now from your remote computer you should be able to connect to: <ip>:<display n> via the Remote Desktop Viewer.

---

