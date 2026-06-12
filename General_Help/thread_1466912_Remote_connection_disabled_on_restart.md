---
title: "Remote connection disabled on restart"
date: 2010-04-30
forum: General Help
---

### Post by Fraoch on 2010-04-30
I had this issue in 9.04, resolved it in 9.10 (it went away on its own), but it's back in 10.04...

I currently run my Ubuntu machine as a headless server and connect to it using TightVNC from a Windows computer.

However, this connection won't work unless I start the Ubuntu machine with a monitor connected.  Once that's done, the remote connection works fine until the Ubuntu machine has to be restarted.  Thankfully Linux doesn't need restarting as much as Windows does, but unfortunately, every time I restart (i.e. with a kernel update, which happened at least a half-dozen times with 9.10), I have to plug the monitor in or TightVNC won't be able to connect.

System - Control Centre - Remote Desktop is set to allow remote connections as it should, I haven't altered this on upgrade.

It's like it's some sort of graphics issue - if no monitor is detected on startup, disable the GUI completely...the system runs fine in remote terminal mode over putty, it's serving files fine and running the few server apps I have on it, but nothing over TightVNC.

Any ideas?

Thank you.

---

### Post by Fraoch on 2010-05-06
No ideas?:(

There was a kernel update the other day and sure enough, the GUI was disabled on restart again.

It's frustrating because I know the OS can do it, certain versions have handled this fine.

It'll kind of defeat the purpose if I have to get a KVM switch.

---

### Post by longanduselessname on 2010-05-06
This isn't an answer to your question, but I suggest you use X forwarding through ssh instead of VNC. This is more secure and I find has a much better response time. 

I don't know why VNC, or ubuntu, needs a monitor to work. Is the X server starting up on reboot?

---

### Post by Fraoch on 2010-05-06
Thanks for the response.

> **longanduselessname said:**
> Is the X server starting up on reboot?

Perhaps not - when I plug in a monitor after a restart, the monitor immediately goes into sleep mode and can't be woken up.  It's like the video card isn't generating anything at all.  I don't even get a shell except remotely through TTY.

---

### Post by longanduselessname on 2010-05-06
> **Fraoch said:**
> Thanks for the response.



Perhaps not - when I plug in a monitor after a restart, the monitor immediately goes into sleep mode and can't be woken up.  It's like the video card isn't generating anything at all.  I don't even get a shell except remotely through TTY.


SSH remotely and do "ps aux|grep X" or "ps aux|grep gdm"
ORRRR
```
ps aux|grep "X\|gdm" 
```<-- this does both, looks for the term X or gdm in the process list

GDM is gnome-desktop-manager and it is the process that starts up the X server on bootup.

See if that is running. I just checked on my own machine and it should be.



EDIT: Oh yea, and what version of Ubuntu are you running? Server edition?


FAKE EDIT2:

I again highly recommend you use ssh forwarding. There are window X clients, like Xming, that can handle ubuntu windows. VNC is not encrypted and is also pretty damn slow. I can help you out starting this up. Also I think you don't need an X server running on the host to forward an X application.

---

### Post by Fraoch on 2010-05-07
> **longanduselessname said:**
> SSH remotely and do "ps aux|grep X" or "ps aux|grep gdm"
ORRRR
```
ps aux|grep "X\|gdm" 
```<-- this does both, looks for the term X or gdm in the process list

GDM is gnome-desktop-manager and it is the process that starts up the X server on bootup.

See if that is running. I just checked on my own machine and it should be.

They're both running, although after the kernel update I restarted with a monitor and I have the GUI up.

The test will be whether these are still running the next time I restart.

> EDIT: Oh yea, and what version of Ubuntu are you running? Server edition?

No, regular desktop version, 64-bit edition.

> FAKE EDIT2:

I again highly recommend you use ssh forwarding. There are window X clients, like Xming, that can handle ubuntu windows. VNC is not encrypted and is also pretty damn slow. I can help you out starting this up. Also I think you don't need an X server running on the host to forward an X application.

VNC is working well for me, I do have password protection in place and it works fast for me over a wired LAN.  However I'm always up for learning something new and if this can solve my issue I'm all for it!

---

