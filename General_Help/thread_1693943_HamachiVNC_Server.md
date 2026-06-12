---
title: "Hamachi/VNC Server"
date: 2011-02-23
forum: General Help
---

### Post by RicheX on 2011-02-23
Hello guys,

I started up my server yesterday and I've been wanting to access it by VPN anywhere in the world. Since I got a dynamic IP, I went to no-ip.org and registered + downloaded/installed the client. 

Everything worked great to log in to my computer by local network, and by external network too.

The problem is, the port to access the computer is 5900. My school blocks any ports except 80 and 443. Since those ports are reserved for internet pages/applications, I don't think it is a good idea to change the 5900 port to 80 or 443.

I am also too lazy to build a SSH Tunnel, so I thought of Hamachi. 

My question is : Would it be possible to join my server from an external network by using Hamachi only and the Remote Desktop Server thing that is installed in whithin Ubuntu.

Example :

Set up a Hamachi Ip : 5.165.95.102

On my Windows PC : Launch VNC Viewer and enter : 5.165.95.102.

-----------------------------------------------------------------

I am using Ubuntu 10.10

Would I be able to reach the server this way and get control of it?

---

### Post by junovan on 2011-02-24
You will need to configure it with your Hamachi IP.

I've done it with a game server, and it worked perfectly.
edit: but your server and client (both) must be connected to the same hamachi network, where if you're accessing (school, service, etc.) can install hamachi client, then no problem.

good luck :D

---

