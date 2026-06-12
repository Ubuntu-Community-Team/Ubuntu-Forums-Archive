---
title: "IP Change"
date: 2011-05-24
forum: General Help
---

### Post by ajcurran94 on 2011-05-24
Is it possible to change your IP address if you're using Ubuntu 11.04?

I know that there are a ton of videos on YouTube showing how to change the computer's IP address (using Windows) but I mean the modem/router IP address.

The one that shows up on ipchicken.com

Oh, and if this is the wrong section just say so and I'll post in the right one :)

---

### Post by 5149.5 on 2011-05-24
Your routers external IP address is established when it boots up. Some of the ISPs have a fixed IP address assigned to each customers modem. Other ISPs set the external address randomly and you may be able to acquire a different one by starting the routers DHCP process manually.  Login to your routers admin interface and see if there is a way to reacquire the external address.

---

### Post by Flimm on 2011-05-24
Turning the router off and on again often does the trick, if you're ISP is using DHCP like mine is. If not, you could contact your ISP.

Another option is to use a proxy.

Why do you want to change your IP address?

---

### Post by linuxinstalledfromhdd on 2011-05-24
Changing your IP address is a "hardware" change. Not an OS change. Or OS configuration issue. 

Check it out:

[http://www.youtube.com/watch?v=KJMfazJWDqQ](http://www.youtube.com/watch?v=KJMfazJWDqQ)

Change your MAC ID in your router, and do a power cycle.  

If you are assigned a static IP this will not work for you, probably.  Then you would need to contact your ISP and have them do this for you.

---

### Post by ajcurran94 on 2011-05-24
We have two routers, one that we got from our ISP which is a TP-LINK TD-8840T ADSL2+ Modem-Router and we have a D-Link router for our wireless connection.  I'm not sure if I can connect to the D-Link with an ethernet cable and change it's IP address.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Using a proprietary leased/owned hardware router you contact the ISP for support. Done deal.

---

