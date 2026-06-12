---
title: "How to use a 3g router and normal LAN? (2 NIC's)"
date: 2011-08-31
forum: General Help
---

### Post by Narchie on 2011-08-31
Hi,

I have a 3g router (works pretty much like a normal ADSL router) I am trying to set up for testing purposes and have tried several things to get my ubuntu machine to connect to the internet via the router with no effect.

What would be the best network setup for this?

I already have a LAN connection to our work network that I would like to keep as well.

Basically what I have done thus far is to plug a 2n'd NIC into my computer and plugged the router into that.

The router is on a different IP range from my normal network.

I have tried the following (ip's are changed from what I am using).
The router is already configured to run on vodacom and 3g is active and working. (tested and working on a windows box).

I can get both my work LAN and the 3g router working to the point where I can work on my LAN and can open the router via firefox.

LAN (NIC 0)
IPv4> 111.111.0.11
Subnet> 255.255.255.0
Gateway> 111.111.1.1
DNS> My DNS servers IP Addresses (eg 111.111.0.3 111.111.0.6)
Search Domains> Windowsdomainname.local

3g Router (NIC 1)
IPv4> 111.111.1.11
Subnet> 255.255.255.0
Gateway> 111.111.1.1
DNS>
Search Domains>
Routes> Use this connection only for resources on its network is ticked (no actual routes specified).

I have tried routing as follows but this also did not help: 

NIC0>Routes as follows: 
Address 111.111.0.0
Netmask 255.255.255.0
gateway 111.111.1.1 But this made no difference. 
Both Networks are running but no internet. 						

How do I get this to work?

I would prefer something with a GUI as I still consider myself an amateur when it comes to Linux.

Thank you in advance 						

Sean :)

---

