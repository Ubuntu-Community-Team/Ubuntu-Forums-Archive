---
title: "Unable to set up vnc using remote desktop"
date: 2010-11-27
forum: General Help
---

### Post by evan4321 on 2010-11-27
Hello,

I am Trying to set up my desktop in order to access it from a remote computer using Remote desktop. I have ubuntu 10.10 and am using the included software remote desktop. When I run the programm is says i can only connect locally using the name "local host". I am trying to connect to my desktop from a vnc app on my ipod touch. It asks me for the ip address and the port. PLEASE HELP!!!!!!

---

### Post by lmarmisa on 2010-11-28
> **evan4321 said:**
> Hello,

I am Trying to set up my desktop in order to access it from a remote computer using Remote desktop. I have ubuntu 10.10 and am using the included software remote desktop. When I run the programm is says i can only connect locally using the name "local host". I am trying to connect to my desktop from a vnc app on my ipod touch. It asks me for the ip address and the port. PLEASE HELP!!!!!!

Welcome to the forums.

I attach two captures of the remote access menu:

1) This configuration allows the remote access to your desktop ONLY from your LAN.

2) This alternative configuration allows the remote access to your desktop not only from your LAN but also from Internet. The difference is the selected option "configure network automatically to accept connections". This options will work properly only if your router supports the [UPnP]("http://en.wikipedia.org/wiki/Universal_Plug_and_Play") feature (for port forwarding) and it is enabled.  Your remote VNC client (located in Internet) will need to know your public IP address or your domain name in order to connect to your VNC server. Consider to use a [Dynamic DNS service]("http://en.wikipedia.org/wiki/Dynamic_DNS") like [http://www.dyndns.com/](http://www.dyndns.com/) or [http://www.no-ip.com/](http://www.no-ip.com/) . They offer this service for free.

Finally, an important warning: enable the remote access to your desktop from Internet ONLY if it is absolutely necessary. This option is potentially less secure and more dangerous in relation with attacks from Internet.

---

