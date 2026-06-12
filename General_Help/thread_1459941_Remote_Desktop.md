---
title: "Remote Desktop"
date: 2010-04-22
forum: General Help
---

### Post by kroko.kroko on 2010-04-22
Hi All,

I have big problem and cannt solve It.

I want to make remote desktop connection between two ubuntu 9.04. I go to System > Preferences > Remote Desktop, mark all two boxies in Sharing and I get:

Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

Just LOCALHOST! I need to have there a IP too.

Know someone there is the problem?

Thanks

---

### Post by Elaztic on 2010-04-22
Hi, didn't quite catch if both computers were on same network.
If so you can get their IP with the command:
ifconfig

If not then you need the external IP of the other network and then map a port to the computer you want to connect to.
I am not sure how secure RDP is but I would recommend setting up a VPN or use SSH.

---

### Post by nothingspecial on 2010-04-22
Go Applications > Internet > Remote Desktop Viewer

The other computer should be listed in there.

Unless you actually want to view the desktop, I would use ssh instead.

---

### Post by kroko.kroko on 2010-04-22
Actually I need Remote Desktop...

I try'd ssh and I have no problem to make connection between my two Ubuntu. But remote desktop (VNC) refuse the connection.

I find out what VNC server listen not on port 5900, but 5901. So I try'd vncviewer IP:5901 and I get some results. The vncserver Ubuntu dont promt me for allowing connection but vncviewer Ubuntu get me to the terminal of vncserver Ubuntu. But I has not Remote Desktop.

I try'd to connect to me litle network notebook with Debian squeeze. There mark both box in System > Preferences > Remote Desktop > Shares, and I get not only localhost posibility, but the IP adress. The Remote Desktop to this Debian notebook run out of box from both Ubuntu (vncviewer).

Can you push mi a step further?

---

