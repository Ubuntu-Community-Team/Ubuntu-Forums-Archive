---
title: "Help with Minimal Desktop install and Remote Desktop"
date: 2011-04-08
forum: General Help
---

### Post by jubei52 on 2011-04-08
Hello,

I am trying to setup my HTPC.  I wanted to have the most minimal overhead possible so I installed Ubuntu 10.10 server from the mini.iso and just added the ssh option.  I then used the following command to give me a desktop environment because I will want to run firefox and it apparently requires this to run.

Here is the command that I ran:

apt-get install xorg gnome-core gdm gnome-applets gnome-system-tools gnome-utils ubuntu-artwork compiz-gnome firefox sysv-rc-conf

The desktop works fine and I can open fire fox, however, the remote desktop is missing from the preferences menu.

How can I install this?  I would like to add the remote desktop option from a command line.

Thanks.

---

### Post by randallecook on 2011-04-08
Are you talking about the remote desktop protocol and viewing software for it, like one might use to control a Windows desktop from another machine?

If so, look at the rdesktop, grdesktop, tsclient, grcm, and xrdp packages. Maybe they are what you are looking for.

I typically run a Linux desktop and invoke rdesktop to control Windows machines when necessary. The clipboard can be a little sketchy, and video over RDP is not recommended, but otherwise it works pretty well. RDP is a surprisingly efficient protocol.

---

### Post by jubei52 on 2011-04-10
> **randallecook said:**
> Are you talking about the remote desktop protocol and viewing software for it, like one might use to control a Windows desktop from another machine?

If so, look at the rdesktop, grdesktop, tsclient, grcm, and xrdp packages. Maybe they are what you are looking for.

I typically run a Linux desktop and invoke rdesktop to control Windows machines when necessary. The clipboard can be a little sketchy, and video over RDP is not recommended, but otherwise it works pretty well. RDP is a surprisingly efficient protocol.

Thanks very much for your reply!

Actually, I was looking for the opposite - I am using a windows 7 laptop right now and I want to be able to have a remote desktop session onto my Linux machine.  

Will the above options enable me to to do this if I install them?

Thanks.

---

### Post by randallecook on 2011-04-12
What you need is a remote desktop server running on your Linux machine. The remote desktop client will run on your Windows laptop.

I am not sure that remote desktop is necessarily the right approach to use in your situation. It can probably be made to work, but there are two other approaches you might consider.

The first is X windows. This is the native graphics system of Linux (regardless of GNOME or KDE), and it follows a client-server model. You can have putty (an ssh client for Windows, among others) maintain an X windows link ("X forwarding"), and then run an X windows client on your Windows machine. I have done this with some success to run individual Linux apps like gedit, etc., but I have never attempted to forward the entire desktop, although I suspect that that is possible.

The other option is a VNC connection. VNC is a protocol for controlling GUIs remotely. It automatically gives you the entire desktop, and works by sending the changing portions of the remote screen over the network as bitmaps. As such, it is very general, but slower than X windows or remote desktop, which merely send lightweight graphics commands for most operations. Look for instructions on setting up a VNC server on your Linux machine, and getting a VNC client for Windows.

A caution about VNC: unlike remote desktop and X windows, which basically create separate a graphical login on your Linux machine, VNC merely takes over the current graphical console login. If you were to be using your laptop in the same room as the Linux machine, you would likely see windows open and close on the Linux machine, and perhaps even see the mouse move onscreen. The other two protocols would give no indication of activity save for hard disk access and CPU load increase.

If you want to forward sound as well, I believe remote desktop can do it, but I am not sure about the others.

Good luck.

---

### Post by jubei52 on 2011-04-18
> **randallecook said:**
> What you need is a remote desktop server running on your Linux machine. The remote desktop client will run on your Windows laptop.

I am not sure that remote desktop is necessarily the right approach to use in your situation. It can probably be made to work, but there are two other approaches you might consider.

The first is X windows. This is the native graphics system of Linux (regardless of GNOME or KDE), and it follows a client-server model. You can have putty (an ssh client for Windows, among others) maintain an X windows link ("X forwarding"), and then run an X windows client on your Windows machine. I have done this with some success to run individual Linux apps like gedit, etc., but I have never attempted to forward the entire desktop, although I suspect that that is possible.

The other option is a VNC connection. VNC is a protocol for controlling GUIs remotely. It automatically gives you the entire desktop, and works by sending the changing portions of the remote screen over the network as bitmaps. As such, it is very general, but slower than X windows or remote desktop, which merely send lightweight graphics commands for most operations. Look for instructions on setting up a VNC server on your Linux machine, and getting a VNC client for Windows.

A caution about VNC: unlike remote desktop and X windows, which basically create separate a graphical login on your Linux machine, VNC merely takes over the current graphical console login. If you were to be using your laptop in the same room as the Linux machine, you would likely see windows open and close on the Linux machine, and perhaps even see the mouse move onscreen. The other two protocols would give no indication of activity save for hard disk access and CPU load increase.

If you want to forward sound as well, I believe remote desktop can do it, but I am not sure about the others.

Good luck.

Thanks for the input - it is more clear to me now.  I am going to try adding "vino" to my command line input - I tried it out on a VMWARE virtual install and it seemed to do what I want.

Cheers!

---

### Post by bodhi.zazen on 2011-04-18
> **randallecook said:**
> A caution about VNC: unlike remote desktop and X windows, which basically create separate a graphical login on your Linux machine, VNC merely takes over the current graphical console login. If you were to be using your laptop in the same room as the Linux machine, you would likely see windows open and close on the Linux machine, and perhaps even see the mouse move onscreen. 

Depends on the vnc server.

x11vnc, and the default vnc server, vino, behave this way.

tightvnc, freenx, and vnc4server do NOT share a desktop.

Alternates to VNC (vnc is not known for security):

For a light weight solution, use ssh -X and forward a panel.

For management of a server, use a web based control panel such as webmin.

---

### Post by jubei52 on 2011-04-26
Thanks very much - that is very helpful!

---

