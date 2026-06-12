---
title: "help to open ports"
date: 2009-10-13
forum: General Help
---

### Post by sickly on 2009-10-13
Hey guys not sure if its ok to post stuff like this here but theirs a lot of smart people here lol, I need some help here on opening my ports for my web server i made. Its working fine locally but not externally. Im using FreeNAS and have set my static ip addresses, diabled dchp, everything is working fine. BUT, for some reason i cant figure out for the life of me how to get these damn ports open so people can access the website from anywhere. On my router (Belkin model F5D7234-4 V-4) i have tried disabling the firewall completely, DMZ, open specific ports, and still no ports are open as far as the Shields Up website says. If anyone has any ideas please let me know, seem like ive tried everything.
Thanks

---

### Post by amingv on 2009-10-14
Disabling the firewall is never a good idea.

If you can access the web server from within your network, then it's probably got to do with NAT rather than closed ports.

In your router configuration look for NAT/NAPT (Network Address (and Port) Translation, Masquerading or Port Forwarding. Configure it to forward TCP requests and traffic to port 80 to your server's IP (same port).

Should be good to go after that.

Make sure all other unused ports are closed, otherwise you may be compromising your internal network.

---

### Post by sickly on 2009-10-14
Thanks for the reply amingv, I was only disabling the firewall just to see if it would work cause i did forward the ports that i needed and it still wasn't working. But I have Finaly found the problem. It was that I had my setup going like this,<Modem,VOIP, then the router>. Now I have it set up, <Modem,Router, then the VOIP box> and opened the correct ports for the VOIP and it is all working fine. My server is finally working from outside my network.

---

