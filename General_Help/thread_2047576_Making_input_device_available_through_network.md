---
title: "Making input device available through network?"
date: 2012-08-25
forum: General Help
---

### Post by Splooshie123 on 2012-08-25
I'm not sure if this is the right section, but oh well.

I am trying to find a way to connect 2 laptops so that the keyboard of one is available as an input device on the other (for a two player game but I don't have a USB keyboard)

Google only results in how to use the same input device on two computers.

I need to connect the other laptop in a way so that its keyboard will be available to Xserver.

---

### Post by TheFu on 2012-08-25
I'm pretty certain that I don't understand your needs, but **Synergy** [http://synergy-foss.org/](http://synergy-foss.org/) might be what you want.  The screen and PC are used for both machines, but only 1 mouse and keyboard are used.

If you really want the X/windows connection, then the mouse, keyboard AND screen will be displayed on the 1st laptop. That is how X-Windows works.  You can accomplish that by connecting via "ssh -X {other-machine-name} {/full/path/to/X-client-program}"  Usually gaming graphics are too complex for X/Windows to keep up. There is work on a low-latency remote desktop protocol called "Spice" [http://www.spice-space.org/](http://www.spice-space.org/) and  [http://www.brianmadden.com/blogs/gabeknuth/archive/2009/06/18/redhat-spice-vs-rdp-vs-ica-performance-video.aspx](http://www.brianmadden.com/blogs/gabeknuth/archive/2009/06/18/redhat-spice-vs-rdp-vs-ica-performance-video.aspx) which can be setup, but it isn't easy at this point.

For a complete remote desktop with the best performance today, I prefer FreeNX over VNC, but VNC is much easier to setup on Ubuntu.

---

### Post by Splooshie123 on 2012-08-25
I think that does the opposite of what I need. I don't need one set of input devices for multiple computers, I need 2 sets of input devices to be accessible to one computer. Sort of like instead of xorg dual screen, it's xorg dual input.

After a lot more time with Google, I found that Xorg's multi-pointer feature is close to what I'm looking for. Now I need a way for it to detect the keyboard and touchpad of a laptop over a network.

---

### Post by Splooshie123 on 2012-08-26
OK, so I found out I can send input events over the network using netcat ("nc").

Problem is, I have no idea how to create a (virtual) device that will be visible to xinput so I can assign it to a second pointer.

---

### Post by TheFu on 2012-08-26
Just be certain you only run nc on a trusted network. It is dangerous to leave that listener up and running.  Anyone on the network can take over the connection and hence the machine.

---

