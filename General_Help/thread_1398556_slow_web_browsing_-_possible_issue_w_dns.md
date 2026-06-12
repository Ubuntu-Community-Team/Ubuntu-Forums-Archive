---
title: "slow web browsing - possible issue w/ dns?"
date: 2010-02-04
forum: General Help
---

### Post by ggtsu on 2010-02-04
For the last week and a half or so I've noticed that web browsing on Ubuntu has all of a sudden become painfully slow. I use chrome, and every time I open a page it seems like it's always "resolving host". Once a host has been resolved, the site seems to run better. This seems to be an issue regardless of which browser I am using. When using the same machine through vista (dual boot), web performance is as fast as always. My other windows machine works fine as well.

Right now my resolv.conf file is using 192.168.1.1 (router) as the nameserver. I am using a router flashed with dd-wrt firmware. I have heard that there may be issues with ubuntu's IPv6 support and dd-wrt, but I haven't found much info on this. I tried adding a couple of different nameservers including my ISP's and google's. I think it may be working a little better, but it still seems much slower than on windows. Before this problem started last week, I was able to browse on ubuntu without any problem. I haven't made any config changes recently, so it's strange that these problems will crop up so suddenly.

---

### Post by timZZ on 2010-02-04
Type in 

ping [www.google.com](www.google.com) and post the results.

---

### Post by Admiral_Payne on 2010-02-04
Do you have the same problem with a different browser (firefox)?
What are your pingtimes to e.g. google.com?
Does it work to access google.com quickly, through the IP address you get from pinging it?
What happens if you use the [OpenDNS servers]("http://en.wikipedia.org/wiki/Opendns#Servers") as nameservers?
What kind of internet connection do you have? Cable, xDSL, Ethernet?
Is your 192.168.1.1 router also the gateway (this is usually the modem) to your ISP?
Does your modem obtain its IP address through DHCP or is it static?
If through DHCP, does it also obtain the DNS servers from your ISP?

---

### Post by ggtsu on 2010-02-04
PING google.com (74.125.45.105) 56(84) bytes of data.
64 bytes from yx-in-f105.1e100.net (74.125.45.105): icmp_seq=1 ttl=54 time=28.2 ms
64 bytes from yx-in-f105.1e100.net (74.125.45.105): icmp_seq=2 ttl=54 time=23.9 ms
64 bytes from yx-in-f105.1e100.net (74.125.45.105): icmp_seq=3 ttl=54 time=22.2 ms
64 bytes from yx-in-f105.1e100.net (74.125.45.105): icmp_seq=4 ttl=54 time=36.8 ms

---

### Post by ggtsu on 2010-02-04
If I use the ip I get from pinging google, the site pops up instantly.

I know I said earlier that things are just as slow w/ firefox, but I decided to spend some time using firefox again. It seems like firefox is much quicker than chrome. Chrome seems to be hanging on the dns lookups much worse than firefox.

---

### Post by Admiral_Payne on 2010-02-04
> **ggtsu said:**
> If I use the ip I get from pinging google, the site pops up instantly.
= DNS problem.

What type of router do you have?
Perhaps it can't handle the nslookup properly for chrome or something... :S

Have you tried hardcoding the OpenDNS servers?

---

### Post by ggtsu on 2010-02-04
> **Admiral_Payne said:**
> = DNS problem.

What type of router do you have?
Perhaps it can't handle the nslookup properly for chrome or something... :S

Have you tried hardcoding the OpenDNS servers?

I'm using a linksys wrt54g router w/ the dd-wrt firmware. I've been running the same router for years, over multiple versions of ubuntu without any major issues.

I'll try opendns and see how that affects things.

---

### Post by Admiral_Payne on 2010-02-04
In that case I assume you have a modem in front of it?
Is that modem in bridge mode?
How do you obtain an IP address from your ISP?
Is there a difference if you have your computer connected wired or wireless?

---

### Post by ggtsu on 2010-02-04
> **Admiral_Payne said:**
> In that case I assume you have a modem in front of it?
Is that modem in bridge mode?
How do you obtain an IP address from your ISP?
Is there a difference if you have your computer connected wired or wireless?

I have a cable modem in front of the router, connecting me to the world. 
The modem is not in bridge mode, as far as I know. 
The router handles obtaining ip addresses from the isp. I just tried plugged in instead of through wireless and performance was exactly the same.

---

### Post by cricka15 on 2010-02-05
> **ggtsu said:**
> For the last week and a half or so I've noticed that web browsing on Ubuntu has all of a sudden become painfully slow.

I'm experiencing the same thing for about the last week with my wireless, windows runs just fine, ubuntu (or in my case xubuntu) runs really slowly, a lot of the time just timing out, seems effect all aspects, not just browsers, synaptic struggled downloading packages and information about updates too. Seems to be intermittent though, just to confuse things even more!!!

Not too sure where to start with investigating/solving networking problems under ubuntu, what tools/apps/commands should I be looking to use?

Could it be from an upgrade that was installed just over a week ago, I tend to just blindly install whatever updates it recommends (default settings of security and recommended updates only though). Is there a way to see what was updated and when?

thanks for any suggestions

---

### Post by DeMus on 2010-02-05
> **ggtsu said:**
> For the last week and a half or so I've noticed that web browsing on Ubuntu has all of a sudden become painfully slow. I use chrome, and every time I open a page it seems like it's always "resolving host". Once a host has been resolved, the site seems to run better. This seems to be an issue regardless of which browser I am using. When using the same machine through vista (dual boot), web performance is as fast as always. My other windows machine works fine as well.

Right now my resolv.conf file is using 192.168.1.1 (router) as the nameserver. I am using a router flashed with dd-wrt firmware. I have heard that there may be issues with ubuntu's IPv6 support and dd-wrt, but I haven't found much info on this. I tried adding a couple of different nameservers including my ISP's and google's. I think it may be working a little better, but it still seems much slower than on windows. Before this problem started last week, I was able to browse on ubuntu without any problem. I haven't made any config changes recently, so it's strange that these problems will crop up so suddenly.

When the problem started, was it after you installed Samba? For me it did. I have the same problem, look at my thread: [_Slow DNS lookup_]("http://ubuntuforums.org/showthread.php?t=1392522")
It turns out in the file /etc/nsswitch.con there is a line which reads:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```
For using Samba and auto mounting network shares the word WINS has to be placed in front of "dns mdns4"
But doing that, and having Samba work fine, my DNS lookup in Firefox and Chrome takes forever.
So, when you also are using Samba look at the file nsswitch.conf in the /etc folder.

---

### Post by Admiral_Payne on 2010-02-05
> **ggtsu said:**
> The modem is not in bridge mode, as far as I know. 
The router handles obtaining ip addresses from the isp. I just tried plugged in instead of through wireless and performance was exactly the same.

Technically, that's not the way it should be. If your modem is not in bridge mode, it'll be in routing mode. Which means that your cable modem is a modem/router, which means that it has a local DHCP server.
Because your router hands out the IP addresses, that one also has a DHCP server. Perhaps you're simply experiencing these problems because the standard gateway is not the same on both of your computers?

---

### Post by ggtsu on 2010-02-05
> **DeMus said:**
> When the problem started, was it after you installed Samba? For me it did. I have the same problem, look at my thread: [_Slow DNS lookup_]("http://ubuntuforums.org/showthread.php?t=1392522")
It turns out in the file /etc/nsswitch.con there is a line which reads:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```
For using Samba and auto mounting network shares the word WINS has to be placed in front of "dns mdns4"
But doing that, and having Samba work fine, my DNS lookup in Firefox and Chrome takes forever.
So, when you also are using Samba look at the file nsswitch.conf in the /etc folder.

I think I did mess around with some samba settings recently, trying to get shares to automount. That line on my nsswitch.conf looks like

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

It has the wins entry, though in a different order (not sure if order is significant). I'll try removing it and see what happens.

---

### Post by ggtsu on 2010-02-05
DeMus You were right, removing wins did the trick. Now web browsing is as fast as in windows. Did you ever have any luck setting up samba mount shares in a dns friendly way? I could really use those shares.

---

### Post by DeMus on 2010-02-06
> **ggtsu said:**
> DeMus You were right, removing wins did the trick. Now web browsing is as fast as in windows. Did you ever have any luck setting up samba mount shares in a dns friendly way? I could really use those shares.

No, I have not. That's my problem to. I still can't figure out how to setup Samba in such a way that it does what it needs to do, without disturbing webbrowsing.
I'm still waiting for a helping hand here.

---

### Post by ggtsu on 2010-02-06
> **DeMus said:**
> No, I have not. That's my problem to. I still can't figure out how to setup Samba in such a way that it does what it needs to do, without disturbing webbrowsing.
I'm still waiting for a helping hand here.

I found that I can still access my windows shares by using the machine's ip address on the network instead of the machine name. In nautilus I'm using smb://xxx.xxx.xxx.xxx. It's working well for me since I only have one windows computer to access and its ip is static.

---

### Post by DeMus on 2010-02-06
> **ggtsu said:**
> I found that I can still access my windows shares by using the machine's ip address on the network instead of the machine name. In nautilus I'm using smb://xxx.xxx.xxx.xxx. It's working well for me since I only have one windows computer to access and its ip is static.

I use grsync for making back-ups of files and folders in 3 computers. I need to have the shared folders mounted automatically otherwise grsync doesn't see them. This does not work now, so making back-ups is out of the question.

I wonder how others do that. So I am still hoping somebody will find this thread and explains how to do it.

---

### Post by Admiral_Payne on 2010-02-06
> **DeMus said:**
> I use grsync for making back-ups of files and folders in 3 computers. I need to have the shared folders mounted automatically otherwise grsync doesn't see them. This does not work now, so making back-ups is out of the question.

Cronjob? :P
Did you set the workgroup name correctly in /etc/samba/smb.conf ?

---

### Post by DeMus on 2010-02-06
> **Admiral_Payne said:**
> Cronjob? :P
Did you set the workgroup name correctly in /etc/samba/smb.conf ?

Yes, all possible settings in the smb.conf file are correct.
In another thread: [_Network problems_]("http://ubuntuforums.org/showthread.php?t=1392522") I explain what I have done so far and what seems to be the problem. I just don't know how to fix it.
Either I have fast DNS lookup while browsing, or I have auto-mounted shared folders in my network, but I can not get both.

---

