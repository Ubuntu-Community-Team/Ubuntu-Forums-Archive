---
title: "Window or Screen sharing application wanted"
date: 2009-09-16
forum: General Help
---

### Post by bogoliubov on 2009-09-16
Hello. When I use my workstation (with Ubuntu) my laptop is often idling, but I could use the extra screen estate of two monitors. So is there some application that will allow me to connect the two computers so that the laptop screen acts only as a secondary screen?

A bit like remote desktop I suppose, but that would clone the desktops I guess? I'd like to get more space only...

---

### Post by badger_fruit on 2009-09-16
> **bogoliubov said:**
> Hello. When I use my workstation (with Ubuntu) my laptop is often idling, but I could use the extra screen estate of two monitors. So is there some application that will allow me to connect the two computers so that the laptop screen acts only as a secondary screen?

A bit like remote desktop I suppose, but that would clone the desktops I guess? I'd like to get more space only...

laptop monitors are hard-wired into the laptop motherboard so you can't exactly use it as a second display, it would work the other way around - ie connect your monitor into the laptop and configure the OS for dual-display.

You can always increase the number of virtual desktops in your desktop ;)

---

### Post by sedawk on 2009-09-16
Instead of using only the local screen (normally
DISPLAY=:0) you can set another DISPLAY and run some
applications on another screen.

There are two more or less easy ways:

1) Run an X-Server on your laptop
2) Run a virtual desktop on the Ubuntu box with VNC (vnc server)
   and view it with a vnc viewer on your laptop.

For 1:
What your laptop needs is a running X-Server.
If you run windows on the laptop you can have a look at
"cygwin" which is free and includes a X-Server
(started with startxwin.sh).
There are other X-Servers for windows but I'm not
aware of any that is free (X-Deep/32 was free once, but
isn't anymore).

If an X-Server is running on the laptop and your
Desktop has permissions to connect this is what
you would do on your desktop on the command line:
```

export DISPLAY=laptop_ip:0.0
firefox http://ubuntuforums.org/

```

For 2:
Alternatively you can run vncserver on your Ubuntu box
to start a virtual desktop (typically DISPLAY=:1).
Then you can run a vnc viewer on the laptop to view that
desktop. Then on the Ubuntu box you would do this:
```

export DISPLAY=:1
firefox http://ubuntuforums.org/

```
(you might have to do some reconfiguration of the default
 vnc server because it doesn't allow network access
 to your Ubuntu box and you might need to set a password
 for vnc using vncpasswd)

---

### Post by bogoliubov on 2009-11-27
Thanks for the help, but it did not work.
I get a
```
Can't open display
```
error message
I can log in to the laptop over ssh..

---

