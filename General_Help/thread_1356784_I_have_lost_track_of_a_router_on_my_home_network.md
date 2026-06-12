---
title: "I have lost track of a router on my home network"
date: 2009-12-16
forum: General Help
---

### Post by sdowney717 on 2009-12-16
I have 2 wireless routers and one is setup as a wireless access point, with DHCP turned off. So I cant see it in the main routers DHCP client table.

Should it be pingable??
I ran a little batch file to ping thru adresses on the network and it did not come up, just my main router and my PC and a network printer and 2 laptops.

So what happened to it?
I can use it to connect wirelessly or if I plug in a desktop internet works.

So I am seriously confused on the ping issue.

anyway here is the output for nmap, laptops are disconnected
scott@scott-desktop:~$ nmap -sP 192.168.1.1-254 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-12-16 14:09 EST
Host 192.168.1.1 is up (0.00089s latency).
Host 192.168.1.100 is up (0.00022s latency).
Host 192.168.1.104 is up (0.0063s latency).
Nmap done: 254 IP addresses (3 hosts up) scanned in 45.42 seconds

---

### Post by sdowney717 on 2009-12-16
I figured out a few things. I went ahead and reset the second wireless router. The LAN is set to start at 10.0.0.1, so any pc plugged in has to be manually set to 10.0.0.2 255.255.255.0 and then it can log into the router.
Enabling remote access (192.168.1.102:8080) works if you simply plug first routers LAN into wan of router 2. You can get Internet, if DHCP is enabled but then your LANS are on separate network addresses. 
So, turn of DHCP, plug only into LAN ports and router is just an access point with whatever wireless security it had when you set it up.

So to administer the router like this is a pain since you have to move cables or set your Ethernet to manual. But once setup not likely to be looked at again for awhile, hence my note here to jog my memory.

perhaps if I had set lan to 192.168.1.115 etc... instead of 10.0.0.1 the default, then it would work. 
I seem to recall trying it and it gave a warning saying they were in use by the other router.

came across this howto
[http://kb.netgear.com/app/answers/detail/a_id/965](http://kb.netgear.com/app/answers/detail/a_id/965)

it looks like you need to restrict the ip assignment range of the primary router and then you can assign an ip on the secondary router to one that matches your network

---

