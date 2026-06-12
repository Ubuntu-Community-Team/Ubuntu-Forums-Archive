---
title: "Virtual access"
date: 2010-01-04
forum: General Help
---

### Post by danm91 on 2010-01-04
Hi guys,
 
I was just wondering if there is any way for me to virtually access my ubuntu running system from a windows pc away from my home?
 
Thanks Dan

---

### Post by Barriehie on 2010-01-04
Have to better define access.  You mean to SSH into it, show a webpage, what???

---

### Post by pricetech on 2010-01-04
We'll also need to know a little about your home network.  You may have to forward ports in a router for example.

---

### Post by jamesisin on 2010-01-04
As mentioned more information is needed to give more specific answers, but in general the answer is yes.

You can set up your network (port forwarding for port 22 and a static IP address; or vpn and dynamic addresses) so that you can ssh into your Ubuntu machine from outside your network.  You will have to install Cygwin (or something similar) to get ssh working on Windows.  (Cygwin is free and works through Windows 7.)

---

