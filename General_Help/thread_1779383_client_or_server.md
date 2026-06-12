---
title: "client or server?"
date: 2011-06-10
forum: General Help
---

### Post by mistertransistor on 2011-06-10
I want to set up a headless machine to run a data-acquisition application. I may well use VNC to remote in to it. Does it need to be a server? What exactly is the difference between a client and a server install? I don't need any special software, just the jre and rxtx + usbserial for comms.
 
Andrew

---

### Post by blueridgedog on 2011-06-10
A desktop install gets the gnome desktop, a server install does not.  Either will work for your purposes. If you need a graphical environment for VNC, the desktop is the way to go.  Otherwise you could just access it with SSH.

---

### Post by rdp870 on 2011-06-10
I second Blueridgedog, but I want to add that if you do install a desktop w/ VNC, I would recommend tunneling the VNC thru SSH. I would also recommend changing the default SSH port (higher than 1024) and using keypair files rather than passwords.

---

### Post by mistertransistor on 2011-06-10
That's very useful. Thanks to both of you.
Andrew

---

### Post by pricetech on 2011-06-10
Another vote for SSH, but I'd recommend using NX from nomachine.com if you want a GUI.  They have a windows client too, in case that would be helpful.

---

