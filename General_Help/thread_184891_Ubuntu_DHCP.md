---
title: "Ubuntu DHCP"
date: 2006-05-30
forum: General Help
---

### Post by dwessell on 2006-05-30
Heyas,

I'm wanting to take a router, and hook it up to a laptop (novel, huh?). But make the laptop, assign an IP to the router, and act as it's internet connection for serving local pages that are hosted on the laptop.. Is that possible, and if so, can someone point me in the right direction?

I'm fine with installing Apache, and what not.. I'm just not sure of how to make the laptop assign the router an IP and become it's gateway.

Thanks
David

---

### Post by kingmonkey on 2006-05-30
You need to plug your laptop into the router WAN port and set it to automatically get IP address.

This page might be of help as a pointer (havent read it myself) 
[http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

---

### Post by dwessell on 2006-05-30
So the laptop will automatically know to assign the IP address to the router, if I plug it in via the WAN port on the router?

Thanks
David

---

### Post by kingmonkey on 2006-05-30
You'll have to install DHCP on your laptop and tell the router to get its "outside" IP by DHCP.

---

