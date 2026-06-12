---
title: "Remote Desktop on Linux that works with Windows and Macs"
date: 2009-12-23
forum: General Help
---

### Post by matthewboh on 2009-12-23
I'm trying to find an open source or even a product that will allow me to do remote support for my clients.  Basically, I'm the only one usually running Linux (Ubuntu) on the desktop, and I have Mac and PC clients to connect to.  Is there a really simple, easy to install set of programs that would allow me to remote desktop to a user's desktop or server or some server program that would allow me to have a web session?  I would really like to see it with some security.

Thanks all

---

### Post by howefield on 2009-12-23
The one I like is Teamviewer, there is no native linux version but it runs well with Wine. You can connect to both windows and mac operating systems, (but not another linux box). It isn't open source, it is a commercial product but there is well featured free version available.

Benefit being that it cuts through most/all connections and so makes it very easy for the client to use.

Or any type of vnc, I like RealVNC, but possibly a little more configuration in some instances for your clients, but maybe you are able to set that up ?

---

### Post by mikem94590 on 2009-12-23
It's hard to tell, because you haven't given a definition for "clients".

In my situation, "clients" means another computer within my company's LAN.  Because of this, simply installing RealVNC or TightVNC on the computer you need to remote control should work.  From there, you will be able to VNC in using the built-in Remote Desktop Viewer.

The VNC protocal offers good encryption support.  I also know that RealVNC (I'm not sure about TightVNC) offers a web interface ([http://hostname:5800](http://hostname:5800)) that requires the Java Runtime Environment.

---

### Post by matthewboh on 2009-12-23
Thanks guys!

And just to be clear - it's offering support and remote desktop to people and machines outside of my LAN - 

Checked out Teamview - that looks great.

---

