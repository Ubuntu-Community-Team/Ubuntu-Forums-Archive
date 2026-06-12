---
title: "Router IP's"
date: 2010-01-04
forum: General Help
---

### Post by nemiux on 2010-01-04
Hey. I'm using some programs that require open ports. I just open port 12345 for it etc. I open it on my router, IP 192.168.1.100, but if I turn other computer first (which is a reason why I have a router) it gets that IP, and I get 192.168.1.101, and I need to change the settings, so the port 12345 would be open for other IP, and it takes time. Is there any way that router would give one computer the same IP, maybe  according to mac or something?
P.S. Don't offer me manual configuration.

EDIT: I'm using WRT54G (Linksys)

---

### Post by HappyFeet on 2010-01-04
> **nemiux said:**
> 
P.S. Don't offer me manual configuration.

Manual configuration is the only way to do it on most routers. You can go into the router and set IP addresses for each computer as you see fit.

---

### Post by pricetech on 2010-01-04
I don't know the specific router but;

Many if not most routers allow a setting which reserves a specific IP address from the DHCP pool to be given only to a specific device, identified by it's MAC address.

Look through your configuration pages on your router and see if you can find the feature.

---

### Post by audiomick on 2010-01-04
> **pricetech said:**
> I don't know the specific router but;

Many if not most routers allow a setting which reserves a specific IP address from the DHCP pool to be given only to a specific device, identified by it's MAC address.

Look through your configuration pages on your router and see if you can find the feature.

This is exactly what I am doing. I was advised by a friend that it is much simpler than setting static addresses on a Linux system, which is what you will have to do if your router doesn't do reserved addresses. Unfortunately, not all of them do. The function is likely to be in "advanced network" or something similar to that.

---

### Post by bodhi.zazen on 2010-01-04
As an alternate you can configure Ubuntu to use a static IP as well.

This is an option in Network manager or you can do it manually.

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

---

### Post by pricetech on 2010-01-04
> **bodhi.zazen said:**
> As an alternate you can configure Ubuntu to use a static IP as well.

This is an option in Network manager or you can do it manually.

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

OP said static IP was not an option.

---

### Post by ttoilleb on 2010-01-04
Link to WRT54G user guide download page.

[http://www.linksysbycisco.com/US/en/support/WRT54G/download](http://www.linksysbycisco.com/US/en/support/WRT54G/download)

Page 4 describes how to set a static ip by mac address.

---

