---
title: "Setting up a LAN only FTP server."
date: 2010-07-16
forum: General Help
---

### Post by winxpuser on 2010-07-16
I would like to setup an FTP server on one my machines running on my local network and I would like to limit the connections to that machine to only those systems located on the same network. I have decided to use vsftp as the server and was wanting to know what I would need to change in the vsftp.conf file to make it so it 

1.) Starts automatically when I boot / reboot the machine.
2.) only allows connections from within the LAN and basically not even show it's existence to the outside world. 

Thanks,
Dave.

---

### Post by tyleruk on 2010-07-16
Just make sure port 21 is blocked by your modem's firewall, that will stop anyone on the internet from accessing your internal ftp server.

---

### Post by winxpuser on 2010-07-16
Thanks for the reply but I am not sure what you mean when you say to block port 21 via the firewall on my router. At the moment I do not have any ports being forwarded with my router is this enough or do I have to specifically tell my router to block port 21 in some way ?

Also, would using a site like [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/) be useful to test such things in the future so I do not have to ask silly questions like this again.

Thx Again,
Dave

---

### Post by John Bean on 2010-07-16
> **winxpuser said:**
> Thanks for the reply but I am not sure what you mean when you say to block port 21 via the firewall on my router. At the moment I do not have any ports being forwarded with my router is this enough or do I have to specifically tell my router to block port 21 in some way ?

If you are behind a NAT router and no ports are forwarded then you are secure. Use one of the web-based probes (see "Shields Up" at [http://www.grc.com](http://www.grc.com) for example) to test.

Edit: I see you've already found one while I was replying :-)

---

### Post by winxpuser on 2010-07-16
Yeah sorry about that I don't know whats wrong with me today I should of thought of the port scanner in the first place to check as the name suggest I am fairly new to linux / ubuntu so I want to make sure I have all my security issues worked out in advance before doing something I shouldn't. 

Thank Again, 
Dave

---

