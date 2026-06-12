---
title: "Squid help.."
date: 2010-01-21
forum: General Help
---

### Post by karthick87 on 2010-01-21
I have configured squid in a single system,and so that i have configured my browser settings to the following ip address 127.0.0.1 and port address to 3128 and all my Access control rules works fine...But when i remove the browser settings no rules are applied and i can able to browse all sites without any restriction..I want to force my browser to go through the proxy..Is there any way to do this???

---

### Post by Barriehie on 2010-01-21
> **getyourkarthick said:**
> I have configured squid in a single system,and so that i have configured my browser settings to the following ip address 127.0.0.1 and port address to 3128 and all my Access control rules works fine...But when i remove the browser settings no rules are applied and i can able to browse all sites without any restriction..I want to force my browser to go through the proxy..Is there any way to do this???

If you remove the browser settings then you're bypassing squid!  FF, or whatever you're using, will direct connect to the internet and won't be making the requests via the port squid is monitoring.  The rules are still being applied, you're just sidestepping the gate so to speak.

I've currently got squid blocking about 1.6E6 sites and it updates every week!  Cool thing is squid. 8)

---

### Post by chuina on 2010-01-21
There are some stuff in [_[COLOR="Teal"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1099532&page=2") thread.
It might help you.

Also, I'm looking for more solution, cause I'll use squid soon.

---

### Post by chuina on 2010-01-21
OK.
I find a more simpler way of redirecting incoming request of port 80 to port 3128 in my PC.:KS

Use your browser and go to file:///usr/share/doc/iptables/html/NAT-HOWTO-6.html

Look for _6.2 Destination NAT_ > Redirection

Thanks.

---

