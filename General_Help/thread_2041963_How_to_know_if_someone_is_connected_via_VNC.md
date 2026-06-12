---
title: "How to know if someone is connected via VNC"
date: 2012-08-13
forum: General Help
---

### Post by slowmoving57 on 2012-08-13
I often start up X11vnc on my workstation so that I can demonstrate a problem to someone else.  Is there a visual indicator that would let me know if they are still connected?  I'd like to know that they have disconnected before I go on to something else.  I currently run a 

```
ps auwx | grep X11vnc 
```

to see if anyone is connected.

---

### Post by krunge on 2012-09-08
Do you want the x11vnc process to exit when the viewer disconnects (this is the default) or to keep listening?

You could run x11vnc with the "-gui tray" (or "-gui icon") option to give a simple tk icon showing x11vnc's status. It changes color when a viewer is connected. You will probably have to apt-get the "wish" or (preferred) "wish8.4" package for this to work.

From the cmdline you can run the x11vnc remote control "x11vnc -Q clients" to list the connected clients.  Or "x11vnc -Q ping" to see if x11vnc is still there (basically the same as the ps you run)

BTW, going the other way you might want to try the "-accept popup" x11vnc option.  This way you (sitting at the physical display) will have to click "yes" in a popup window to allow the incoming connection to proceed.

---

