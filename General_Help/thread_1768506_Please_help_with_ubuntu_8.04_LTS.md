---
title: "Please help with ubuntu 8.04 LTS"
date: 2011-05-26
forum: General Help
---

### Post by zer0net on 2011-05-26
Hi everyone,
I have Ubuntu 8.04 running virtualmin email server for my small company. I have two 24 port gigabit switches, one of the switch is a "smart switch" (so I can configure it from its web interface, though I havent, it is running out of the box).
The weird problem i'm having is that, if I restart my ubuntu box, it gets IP from router (pfsense) but it cant connect to the internet, nor can it ping anyone else on the network except router. I have to reboot both switches for the ubuntu to connect to the internet :confused:, I dont this problem with any of my windows boxes. BTW, the ubuntu box is plugged into regular switch not in the smart switch.

Can anyone please help?

Thank you

---

### Post by wildmanne39 on 2011-05-27
> **zer0net said:**
> Hi everyone,
I have Ubuntu 8.04 running virtualmin email server for my small company. I have two 24 port gigabit switches, one of the switch is a "smart switch" (so I can configure it from its web interface, though I havent, it is running out of the box).
The weird problem i'm having is that, if I restart my ubuntu box, it gets IP from router (pfsense) but it cant connect to the internet, nor can it ping anyone else on the network except router. I have to reboot both switches for the ubuntu to connect to the internet :confused:, I dont this problem with any of my windows boxes. BTW, the ubuntu box is plugged into regular switch not in the smart switch.

Can anyone please help?

Thank you
Hi, I am sure for the most part everyone will recommend that you upgrade to a newer version that one is far out of date. I wish I could be of more help, I would not have recommended it but I see no one else as posted.

---

### Post by zer0net on 2011-05-27
Thank you for reply, I have been meaning to upgrade, but before I do that I intend to setup a test machine and try to migrate all the servers and data to the new one to see how smooth that goes and if any problem before I actually do it on the production machine.

Thanx again

---

### Post by psusi on 2011-05-27
Please describe the network topology.  You mention two switches, and a router.  How are they connected to each other?

---

### Post by LordNeo on 2011-05-27
Also check if you can ping some outside IP (like 200.1.123.3) to discard any DNS/Routing issues.
I guess the router is giving the DHCP and DNS, but it worths checking

---

### Post by zer0net on 2011-05-27
> **psusi said:**
> Please describe the network topology.  You mention two switches, and a router.  How are they connected to each other?

Hi,
Please see the picture attached,
What I did is, I have DSL Modem going into WAN port of pfsense and then I have LAN port of Pfsense connected to a switch, and within that switch I have bunch of computers connected, I ran out of ports so I bought another switch(smart switch) and I connected the port 24 to port 24 of my other switch and I connected some more computers in that new switch.

Thats about it. Hope that helps.

---

### Post by zer0net on 2011-05-27
> **LordNeo said:**
> Also check if you can ping some outside IP (like 200.1.123.3) to discard any DNS/Routing issues.
I guess the router is giving the DHCP and DNS, but it worths checking

Its weird but I can only ping the router and no other box on the network and nothing on the internet either.

---

### Post by zer0net on 2011-05-27
Any suggestions??? anyone?

---

### Post by psusi on 2011-05-29
And you are sure that these two switches are JUST L2 switches, and not L3 switches/routers?

---

### Post by katykat on 2011-05-29
What you need to do is set the 'smart switch' to the same IP of the original router, typically 192.168.0.1. And that it has anything remsembling a DHCP server turned OFF.  

Others may be more kmowledgeale about this, but I ran into a similar problem hooking up a second router. 

You may be able to get it to work by NOT using the 'uplink' port on the second router/switch. 

Eventually I got rid of the second router, and used a 'simple' basic switch, and have had no problems. 

Yours may be too smart for its own good....

Other than that, if it works, dont fix it - especially in a business environment. 

I found just trying to get from 9.04 to 10.04 to be a total nightmare, and needed to format and start afresh. Fortunately 10.10 had just come out, and is remarkably stable over 9.04 which was always problematical.

---

### Post by psusi on 2011-05-29
A switch does not have an IP address, if it does, then it's a router.  If you can disable the routing functions and get it to just behave as a switch, then do that.

---

### Post by zer0net on 2011-05-29
The smart switch does have an IP thats how I access it to configure it from its web interface. The other switch does not have an IP its just a switch. As far as I know the smart switch does not have a DHCP server and all the IP leasing is handled by the pfsense router.

Setting smart switch to the same IP as router may cause conflicts. wont it?

---

### Post by psusi on 2011-05-30
It sounds like the switch does have DHCP enabled, and so when you think the Ubuntu machine is getting its IP address from the router, it actually got it from the switch, which is why it can't communicate with anyone.

---

### Post by zer0net on 2011-06-10
so it turns out that its not the switches or router that was causing this, there seems to be a rouge DHCP running on one of the computers on network which was screwing everything up.

now its all fixed, thank you everyone for your help.

---

