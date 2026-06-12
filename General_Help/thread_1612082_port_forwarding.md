---
title: "port forwarding"
date: 2010-11-02
forum: General Help
---

### Post by spiky001 on 2010-11-02
Ok i want to access my server from internet, ok I have checked with my mobile internet provider (3) they say they dont block any ports, is it just a case of letting the firewall let external access to pc? ( no router just mobile dongle)And do i just ssh into external ip on ssh port

---

### Post by krink on 2010-11-02
I access my computer at home frequently through ssh, its just a matter of installing the ssh server. You can change it to whatever port you like however you will need to allow this as an acceptation on your router (it differs between brands and models). You will need a static ip and it  will be easiest if you assign it one through something like no-ip.org. Once you have ssh access, you can pretty much access anything you want.

---

### Post by spiky001 on 2010-11-02
I have ssh set up on lan all works, Just I will need to use it from else where, I know about  static ip and I dont have a router, so I presume the firewall is stopping access. So do I just set firewall to allow external incoming connections? then do I connect via external ip to my ssh port eg external ip 188.xxx.xx.xx port 22, although the server ip is 10.42.xxx.xx internal

---

