---
title: "After upgrade to 10.04, cannot load web pages"
date: 2010-06-30
forum: General Help
---

### Post by Driagan on 2010-06-30
Yesterday I upgraded from 9.10 to 10.04 using the built in upgrader. 

After upgrading, whenever I open Firefox, it will just say "The connection has timed out" for every page, but I am connected to the internet. Also, w3m will not load any web pages as well. But I am connected to the internet, because pidgin works, apt-get works, ping, and telnet work.

I will ping google.com with success each time, then attempt to load google.com in Firefox and it will say that it cannot connect to the host. I have tried both "Connect directly to the internet" and "Connect using system proxy settings" for Firefox (the system settings are to connect directly to the internet).

I then thought that maybe something was blocking port 80, so I used telnet (telnet google.com 80), and with that, I got the HTML response of google.com.

My question is, what can I do to make my computer able to brows the web again?

I am running Ubuntu 10.04 with kernel 2.6.32-22 on a Compaq Presario CQ60-417DX Notebook. 
Processor: Intel Celeron 900 @ 2.20 GHz
RAM: 3.00 GB

---

### Post by Driagan on 2010-06-30
Anyone have any ideas?

---

### Post by Driagan on 2010-06-30
After messing around, I found out that I can load pages in the form of [http://82.105.36.210/](http://82.105.36.210/) but not [http://elart.it/](http://elart.it/)

So, I figured that it was probably something with my DNS, so I went to about:config and searched for DNS, and found network.dns.disablelPv6, I changed that from false (the default value) to true, and vuala, I can now load pages in firefox!

---

### Post by lovinglinux on 2010-06-30
> **Driagan said:**
> After messing around, I found out that I can load pages in the form of [http://82.105.36.210/](http://82.105.36.210/) but not [http://elart.it/](http://elart.it/)

So, I figured that it was probably something with my DNS, so I went to about:config and searched for DNS, and found network.dns.disablelPv6, I changed that from false (the default value) to true, and vuala, I can now load pages in firefox!

Yes, that is the solution I would suggest, but I wasn't fast enough :)

You can also disable it system wide. See [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

