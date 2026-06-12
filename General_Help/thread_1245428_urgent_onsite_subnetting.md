---
title: "urgent onsite subnetting"
date: 2009-08-20
forum: General Help
---

### Post by sefs on 2009-08-20
hi all need some quick help

i have a network 172.16.0.0 with subnet mask of 255.255.0.0

the adsl modem/router has ip 172.16.254.0  but i cannot choose a subnet mask of 255.255.0.0

it has it set out like 255.255.255.0
255.255.255.128 and so on in that format from a list box

wich of those settings are equiv to 255.255.0.0 so we can get these two subnets talking


thanks

---

### Post by epsolon77 on 2009-08-20
> **sefs said:**
> hi all need some quick help

i have a network 172.16.0.0 with subnet mask of 255.255.0.0

the adsl modem/router has ip 172.16.254.0  but i cannot choose a subnet mask of 255.255.0.0

it has it set out like 255.255.255.0
255.255.255.128 and so on in that format from a list box

wich of those settings are equiv to 255.255.0.0 so we can get these two subnets talking


thanks

The subnet gateway IP should be 172.16.0.1 for your router, if I remember my subnetting correctly.  Someone please correct me if I am wrong.

---

### Post by sefs on 2009-08-21
Ok let me explain better now I am out of the fire...

The LAN is sitting on the subnet 172.16.0.0/255.255.0.0

All machines have the IP's 172.16.0.x.  The DNS for the LAN is 172.16.0.1.

All machines on the lan have static IP's

the Gateway is 172.16.254.254 (i.e it sits on the subnet 172.16.254.0/xxx.xxx.xxx.xxx) I have no idea what the netmask was.

The situation is that the gateway (provider adsl modem/router) went bum and got thrown out, so I can't see what the settings were, and a new modem put in its place

So I set the modem IP back to 172.16.254.254/255.255.255.0 but realized that the LAN (172.16.0.0/255.255.0.0) could not ping the router, so no inet access for them.

So I went to set the router netmask to 255.255.0.0 to see if it would be seen from 172.16.0.0/255.255.0.0 but no cigar it only allows me to set the netmask to a list like the one below:

255.255.255.0
255.255.255.128
255.255.255.224
...

and so on 

I set it to 255.255.255.128 and lost all connection to the modem admin webpage. I had to reset it to factory defaults.

So I was asking what netmask the modem had to be at to be sitting on a 172.16.254.0/xxx.xxx.xxx.xxx network and be accessible from a 172.16.0.0/255.255.0.0 network.

What I did temporarily was to make the modem 172.16.0.254/255.255.255.0 and on the clients change all their gateway settings to 172.16.0.254.  BUT I want to put back things the way I found them, which is to have the clients on their original settings (pointing to a gateway of 172.16.254.254), and the gateway with its original IP of 172.16.254.254/xxx.xxx.xxx.xxx

Thanks.

---

### Post by epsolon77 on 2009-08-21
Please forgive me if I am incorrect because it has been a while since I've been throguh complex routing...but your gateway should NOT be able to be a part of the 255.255.0.0 subnet with an IP of 172.16.254.254 because it has already been specified as a member of 172.16.254.x.  Specifying a number other than 0 in the third octet should limit the device from seeing other subnets, without a specified route to the other subnets gateways.  Specifying the Subnet as 255.255.255.128 would limit the routers ability to be seen further.  If the router needed to be set at 172.16.254.254, you could add static routes to allow the router to respond to different subnets, but I don't see why you would want to.

I am sure there is a reason for setting the IP to 172.16.254.254, but I would leave the IP at 172.16.0.1 or 172.16.0.2 if there is a complication with another server.

---

### Post by sefs on 2009-08-21
> **epsolon77 said:**
> Please forgive me if I am incorrect because it has been a while since I've been throguh complex routing...but your gateway should NOT be able to be a part of the 255.255.0.0 subnet with an IP of 172.16.254.254 because it has already been specified as a member of 172.16.254.x.  Specifying a number other than 0 in the third octet should limit the device from seeing other subnets, without a specified route to the other subnets gateways.  Specifying the Subnet as 255.255.255.128 would limit the routers ability to be seen further.  If the router needed to be set at 172.16.254.254, you could add static routes to allow the router to respond to different subnets, but I don't see why you would want to.

I am sure there is a reason for setting the IP to 172.16.254.254, but I would leave the IP at 172.16.0.1 or 172.16.0.2 if there is a complication with another server.

The IP was never 172.16.0.1 for the router.  That is the IP of the Domain Server.

Thanks.

---

### Post by capscrew on 2009-08-21
> **sefs said:**
> hi all need some quick help

i have a network 172.16.0.0 with subnet mask of 255.255.0.0

the adsl modem/router has ip 172.16.254.0  but i cannot choose a subnet mask of 255.255.0.0

This is a /16 bit subnet mask.  The range of addresses spans that last 2 octets.  That would make the network 172.16.x.x and the IP addresses x.x.0.1 to x.x.255.255.  More than you will ever need at home. > 

it has it set out like 255.255.255.0
255.255.255.128 and so on in that format from a list box

The first one is a 24 bit mask making the last octet the IP range x.x.x.1 to 254.  The second one is a /25 bit range and it limits you to half the octet.  Which half is your choice e.g 172.16.0.0/25 gives you an IP range of x.x.x.1 to 127 or an IP range of x.x.x.128 to 255 > 

wich of those settings are equiv to 255.255.0.0 so we can get these two subnets talking

Neither one!  You can change either the IP address of the new device or the IP addressing scheme of your network to accommodate the limitations.  If the new device is truly incapable of understanding a 16 bit mask, then you are best off configuring everything to a 24 bit scheme.

You can do one of 2 things.  Get a modem that understands larger network subnet masks or reconfigure your network.  The second choice would require that you -- a. change the IP address of the modem and -- b. change your network subnet mask to 255.255.255.0 (a 24 bit mask).

---

### Post by sefs on 2009-08-21
> **capscrew said:**
> This is a /16 bit subnet mask.  The range of addresses spans that last 2 octets.  That would make the network 172.16.x.x and the IP addresses x.x.0.1 to x.x.255.255.  More than you will ever need at home. The first one is a 24 bit mask making the last octet the IP range x.x.x.1 to 254.  The second one is a /25 bit range and it limits you to half the octet.  Which half is your choice e.g 172.16.0.0/25 gives you an IP range of x.x.x.1 to 127 or an IP range of x.x.x.128 to 255 Neither one!  You can change either the IP address of the new device or the IP addressing scheme of your network to accommodate the limitations.  If the new device is truly incapable of understanding a 16 bit mask, then you are best off configuring everything to a 24 bit scheme.

You can do one of 2 things.  Get a modem that understands larger network subnet masks or reconfigure your network.  The second choice would require that you -- a. change the IP address of the modem and -- b. change your network subnet mask to 255.255.255.0 (a 24 bit mask).

Good show.  As I've temporarily put the modem into the same subnet as the network and changed the nodes gateway to point to that new IP, I think I'll just leave it at that.

Thanks for the help guys.

---

### Post by capscrew on 2009-08-21
> **sefs said:**
> Ok let me explain better now I am out of the fire...

The LAN is sitting on the subnet 172.16.0.0/255.255.0.0

This is can be stated as 172.16.0.0/16> 

All machines have the IP's 172.16.0.x.  The DNS for the LAN is 172.16.0.1.

If you are only using the last octet, i.e. x.x.x.1 to 255 then you can safely change your subnet mask to 255.255.255.0 (a 24 bit mask) without any problems. > 

All machines on the lan have static IP's

the Gateway is 172.16.254.254 (i.e it sits on the subnet 172.16.254.0/xxx.xxx.xxx.xxx) I have no idea what the netmask was.

Assign it a new IP addres in the 172.16.0.0/24 range.  I would use 172.16.0.254 myself.> 

The situation is that the gateway (provider adsl modem/router) went bum and got thrown out, so I can't see what the settings were, and a new modem put in its place

So I set the modem IP back to 172.16.254.254/255.255.255.0 but realized that the LAN (172.16.0.0/255.255.0.0) could not ping the router, so no inet access for them.

So I went to set the router netmask to 255.255.0.0 to see if it would be seen from 172.16.0.0/255.255.0.0 but no cigar it only allows me to set the netmask to a list like the one below:

255.255.255.0
255.255.255.128
255.255.255.224
...

and so on 

I set it to 255.255.255.128 and lost all connection to the modem admin webpage. I had to reset it to factory defaults.

So I was asking what netmask the modem had to be at to be sitting on a 172.16.254.0/xxx.xxx.xxx.xxx network and be accessible from a 172.16.0.0/255.255.0.0 network.

What I did temporarily was to make the modem 172.16.0.254/255.255.255.0 and on the clients change all their gateway settings to 172.16.0.254.  BUT I want to put back things the way I found them, which is to have the clients on their original settings (pointing to a gateway of 172.16.254.254), and the gateway with its original IP of 172.16.254.254/xxx.xxx.xxx.xxx

Thanks.

Well, I see you came to the same conclusion.  The modem restricts you to a 24 bit subnet mask.  You will always have to live with the 255 IP address range of the last octet if you use this modem.

---

### Post by sefs on 2009-08-21
> **capscrew said:**
> This is can be stated as 172.16.0.0/16If you are only using the last octet, i.e. x.x.x.1 to 255 then you can safely change your subnet mask to 255.255.255.0 (a 24 bit mask) without any problems. Assign it a new IP addres in the 172.16.0.0/24 range.  I would use 172.16.0.254 myself.

Well, I see you came to the same conclusion.  The modem restricts you to a 24 bit subnet mask.  You will always have to live with the 255 IP address range of the last octet if you use this modem.

The modem is a piece of junk.  The previous one had a free form field where you could type your netmask of choice.  This new one only has those pre configured netmask in a drop down box. Such is life.

---

