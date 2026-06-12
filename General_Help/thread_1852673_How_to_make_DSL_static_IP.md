---
title: "How to make DSL static IP?"
date: 2011-09-30
forum: General Help
---

### Post by markomk on 2011-09-30
Hi,
I don't have big experience with Ubuntu so I need little help :)
My laptop is connected on my wireless router, I didn't want to be on that network so I open pppoeconf DSL connection. The problem is everytime I reboot my laptop I will have dynamic IP. How can I make to have static IP?

Thank you,
Marko :)

---

### Post by papibe on 2011-09-30
Which version of Ubuntu do you have?

If you want to have a LAN static IP you have two options:
[LIST=1]
[*]set it in your router, or
[*]use 'Network Connections' in your computer.
[/LIST]
In your machine: Open Network Connections. There select either if you are using a wired or wireless connection. Then select your interface and press edit. Then go to the IPv4 tab, and change the method to 'Manual'. Set the rest of the fields.

Although, If by this you mean something else
> I didn't want to be on that network...
You would need to explain a little but more.

Regards.

---

### Post by seawolf167 on 2011-09-30
Take a look at [this link ]("http://www.liberiangeek.net/2011/03/configure-permanent-static-ip-addresses-ubuntu-11-04-natty-narwhal/")and see if it helps you. Just edit your wireless connection vs. your ethernet connection.

---

### Post by markomk on 2011-09-30
> **papibe said:**
> Which version of Ubuntu do you have?

If you want to have a LAN static IP you have two options:
[LIST=1]
[*]set it in your router, or
[*]use 'Network Connections' in your computer.
[/LIST]
In your machine: Open Network Connections. There select either if you are using a wired or wireless connection. Then select your interface and press edit. Then go to the IPv4 tab, and change the method to 'Manual'. Set the rest of the fields.

Although, If by this you mean something else

You would need to explain a little but more.

Regards.

Yes, few days ago I suspect someone get access in my pc(windows) somehow I figureout and close all connections, my pc was connected through my router(I hate windows but I must use because some programs). 
On my laptops I have Linux Ubuntu, so I don't want with cable to connect to router, I connected by wireless, after I created DSL connection so I have different IP than my router(not local like 192.168.0.100) but direct connection.
I also set my router "Use as a DSL modem) not like router. 
So, I will get dynamic IP and all I want to is static IP, I don't want to my IP to be changed on rebooting or dropped connection.

Sorry for my poor English :)

I hope you understand my point.

---

### Post by markomk on 2011-09-30
> **seawolf167 said:**
> Take a look at [this link ]("http://www.liberiangeek.net/2011/03/configure-permanent-static-ip-addresses-ubuntu-11-04-natty-narwhal/")and see if it helps you. Just edit your wireless connection vs. your ethernet connection.

This is LAN static IP, I want my direct connection ex. 77.28.40.99 to be my permanent IP.

---

### Post by lisati on 2011-09-30
The IP address you have given looks like one that will have been assigned by your ISP, and is separate from the IP addresses allocated on your home network.

My personal preference is to assign a static IP address for each of the devices connected to my modem/router through the router's browser-based control panel, rather than trying to do it from the computer. That way, for example, if I hook up my laptop to someone else's network (maybe when I'm at work) I'm less likely to run into IP address allocation conflicts. How to do this depends on the specific router.

---

### Post by markomk on 2011-09-30
> **lisati said:**
> The IP address you have given looks like one that will have been assigned by your ISP, and is separate from the IP addresses allocated on your home network.

My personal preference is to assign a static IP address for each of the devices connected to my modem/router through the router's browser-based control panel, rather than trying to do it from the computer. That way, for example, if I hook up my laptop to someone else's network (maybe when I'm at work) I'm less likely to run into IP address allocation conflicts. How to do this depends on the specific router.

Well from my laptop Ubuntu, First I need to connect to my router  ex. 10.0.0.1, by my wlan0(without connection to my router I can't establish DSL connection)and then to create pppoeconf. So, router IP(ex. 77.24.44.120) and my laptop IP(ex.77.24.44.30) are different.
If somehow helps I can put picture how is connected.

[[img]http://s2.postimage.org/13hapi6p0/dsl.jpg[/img]](http://postimage.org/image/13hapi6p0/)

So my Laptop will use the router only to create DSL connection and get new IP.

---

