---
title: "Screen Sharing"
date: 2009-07-14
forum: General Help
---

### Post by Tclarkie on 2009-07-14
Anyone know how toscreenshare over the internet in ubuntu, (preferably to a mac)

---

### Post by JohnnySage50307 on 2009-07-14
Set up a Remote Desktop server.  Go to System->Preferences->Remote Desktop and activate it; make sure you enable it with a password, otherwise anyone can hack in.

Get your IP address (ifconfig helps, but for whatever reason on my network it only gave me the local address).  Open your router (usually you can go through an internet browser and use the address 192.168.1.1), find your machine, and make sure you have either Remote Desktop or VNC ports open (namely port 5900 TCP).  Open a remote desktop client or a VNC client.  If you use a VNC client, make sure you add ":5900" at the end of your IP address.  Voila!

---

### Post by Tclarkie on 2009-07-14
Is that over the net or just a home network?

---

### Post by Seed++ on 2009-07-14
Teamviewer.

---

