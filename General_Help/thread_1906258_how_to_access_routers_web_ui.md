---
title: "how to access routers web ui"
date: 2012-01-08
forum: General Help
---

### Post by hg088 on 2012-01-08
i followed a tutorial to get my router working as a switch.

it said that i had to turn of dhcp and set mode to routing.

it worked great and know my router is working as a switch as i wanted but, now i dont know the ip of my router/switch to access the web ui

its not 192.168.1.1 or 192.168.0.1

i really wish someone could tell me how to access the web ui without having to reset the router/switch

---

### Post by Double.J on 2012-01-08
> **hg088 said:**
> i followed a tutorial to get my router working as a switch.

it said that i had to turn of dhcp and set mode to routing.

it worked great and know my router is working as a switch as i wanted but, now i dont know the ip of my router/switch to access the web ui

its not 192.168.1.1 or 192.168.0.1

i really wish someone could tell me how to access the web ui without having to reset the router/switch

Hi there, have you tried numbers ranging from 192.168.1.0 to 192.168.1.10? I was wondering if you set it up as a switch that you may have another router set as 192.168.1.1? typically the other addresses on the network only change the last number- for example, my router is 192.168.1.1, my desktop is 1.2, my bridge is 1.3 and the upstairs pc is 1.5 ... i don't know why 4 is unassigned!

---

### Post by Triblaze on 2012-01-08
To find your router's IP, you could perform a traceroute. The first hop should be your router's ip.

You can enter "traceroute www.google.com" (or another site) in the terminal, or use the networking tools in the System administration menu.

---

### Post by hg088 on 2012-01-08
hi thanks for the reply

i think my problem is that my router is not using private ip's anymore so im guessing it now has a public ip provided by the isp's dhcp server, and i dont know which is

tried scanning my subnet with nmap but it just finds about 15 host and none is my router

another possibility might be that my router doesnt have an ip know, after all, it is supposed to be a switch know right? ^^

---

### Post by hg088 on 2012-01-08
hi thanks for the reply

i think my problem is that my router is not using private ip's anymore so im guessing it now has a public ip provided by the isp's dhcp server, and i dont know which is

tried scanning my subnet with nmap but it just finds about 15 host and none is my router

another possibility might be that my router doesnt have an ip know, after all, it is supposed to be a switch know right? ^^

---

### Post by wh33t on 2012-01-08
> **hg088 said:**
> hi thanks for the reply

i think my problem is that my router is not using private ip's anymore so im guessing it now has a public ip provided by the isp's dhcp server, and i dont know which is

tried scanning my subnet with nmap but it just finds about 15 host and none is my router

another possibility might be that my router doesnt have an ip know, after all, it is supposed to be a switch know right? ^^

Whenever I want to use a router as a switch I just don't plug in the WAN cable to the WAN port. Basically I'm saying I don't connect my cable modem to the WAN port, I connect it to one of the regular computer ports on the router. When this happens my router acts as a switch. 

Most switches don't have Web interfaces because most switches don't have too many options that the regular user would want to adjust (maybe load balancing? traffic shaping?) but it is possible to purchase a "managed switch" as I believe they call them.

---

### Post by Doug S on 2012-01-08
I have one of my hardware routers setup as a switch. As wh33t mentioned, don't use the WAN port. I also set it to a static IP address on the proper sub-net, but outside of the range of IP addresses that would be allocated by the DHCP server upstream. I access the web UI via the static IP address that I gave it.
I also turned off DHCP and NAT on it, but wh33t has an interesting point, and maybe I didn't have to do that

---

### Post by hg088 on 2012-01-08
yeah there probably isnt a way to access the ui while using the router as a switch as i didnt set an static ip :(

i have 6 devices currently connected to the switch and they all have public ip's provided by the isp, which is pretty awesome considering some isps only provide one or two public ips per home :)

> I also set it to a static IP address on the proper sub-net, but outside of the range of IP addresses that would be allocated by the DHCP server upstream
the upstream server assigns public ips, so, is it ok if i set the router/switch ip as private like 192.168.0.1?

thanks for replying guys

---

### Post by electrojustin on 2012-01-08
Have you tried 192.168.2.1?

---

### Post by wh33t on 2012-01-08
> **hg088 said:**
> 
i have 6 devices currently connected to the switch and they all have public ip's provided by the isp, which is pretty awesome considering some isps only provide one or two public ips per home :)

the upstream server assigns public ips, so, is it ok if i set the router/switch ip as private like 192.168.0.1?


Be careful your ISP doesn't charge you for more IP's. I have heard some do this. 

You can have your router have any IP address but if you want to be able to connect to it via the Internet (because you no longer part the Subnet the router creates) your router must have WAN Access enabled. 

But in order to connect to the Router over WAN access it still has to have a connection to the Internet I think (which means plugging in a cable to the WAN port which would probably turn the Router back into routing mode versus Switch mode). So this probably isn't possible. 

Not to mention I'm not sure what you would gain by accessing it as a switch as I'm sure it wouldn't have any switch management features as that's not what it was designed to do.

Just my two cents.

---

### Post by hg088 on 2012-01-08
> Have you tried 192.168.2.1?
yes ive tried all the private ips using nmap too
> e careful your ISP doesn't charge you for more IP's. I have heard some do this.
oh that would be pretty lol xD. i live in venezuela and things are always weird ans messy around here, dont really think (hope xD) they'll charge me for the extra ips, specially since the fastest connection they offer is 1Mbit :(
yep im probably being a bit too creative here xD, ill do some more experimentation tomorrow

thanks again for replying

---

