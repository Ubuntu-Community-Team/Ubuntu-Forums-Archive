---
title: "Synergy behind 2 routers"
date: 2010-02-28
forum: General Help
---

### Post by Elep.Repu on 2010-02-28
Hi. I'm using synergy with an Ubuntu box and a Windows box.

It works fine behind one router, when they're both plugged into the same.
But, I have a ddwrt router in my room, as a client, connecting to the router on the other end of the house. The laptop (running ubuntu) when I input the internal IP of the desktop (running windows), it can't connect unless I'm LAN'd to the same ddwrt router.

That's fine but I normally have the laptop going off the wireless from the other router.

How can I connect the laptop? I've tried the hostname instead of the internal ip but that didn't work. I'm not sure..

Not a huge deal but I'm kind of curious.

---

### Post by cjhabs on 2010-02-28
Are the IP addresses of the 2 routers on the same subnet?
What are the IP addresses of the Windows and Ubuntu boxes?
How are they obtaining their addresses - manually or dhcp?

---

### Post by Elep.Repu on 2010-02-28
> **cjhabs said:**
> Are the IP addresses of the 2 routers on the same subnet?
What are the IP addresses of the Windows and Ubuntu boxes?
How are they obtaining their addresses - manually or dhcp?

The 2 routers are on different subnets. 
The computers obtain their IPs through dhcp. 

Win; 192.168.7.102
linux; 192.168.1.102

---

### Post by pirateghost on 2010-02-28
> **Elep.Repu said:**
> The 2 routers are on different subnets. 
The computers obtain their IPs through dhcp. 

Win; 192.168.7.102
linux; 192.168.1.102
different subnets require you to have a route from one subnet to another in order to use services on the other subnet.

why are they on different subnets?

---

### Post by Elep.Repu on 2010-02-28
> **pirateghost said:**
> different subnets require you to have a route from one subnet to another in order to use services on the other subnet.

why are they on different subnets?

Idk. Someone told me I should change the client router's subnet. I thought that they would conflict.
I'll change it back.

---

### Post by cjhabs on 2010-02-28
Just make sure that both routers are not serving up dhcp addresses, or if they are that the ranges don't overlap. As mentioned, you need the routers on the same subnet unless you do some advanced configuration to set up routing between subnets.

---

### Post by Elep.Repu on 2010-02-28
Ok.

Turns out I lost connectivity after changing the ddwrt client to the same subnet. Restart on windows and router reboot didn't lead anywhere.

I'll look around about routing between different subnets.
I'm not entirely sure whether the router is assigning ip addresses or not, or how to check on that.

---

### Post by pirateghost on 2010-02-28
it sounds like you need to set up the second router as simply a switch and access point.  what it sounds like you have now is that the second one is set up as a router/gateway and you have to have it in a different subnet in order for the routing to work.  you dont need routing on the second one.  assign it a static IP address in the same subnet (cannot be the same address as the other router), disable DHCP on the second router, plug the cable into a LAN port and not the WAN port.  then all your machines behind the second router should be on the same subnet and getting the ip address from the first router.  the second router at this point will just be acting as a switch and access point.

---

### Post by Jared Norris on 2010-03-01
As the previous posters have said you probably just want to set it up with a single router on the one subnet if it's just for your own personal use. Having multiple routers/subnets/dhcp will just make life exceptionally difficult for no real perceived gain.

If you still want to use 2 different routers and are using one router connected through a lan port on another router you will need to look at port forwarding the appropriate port (default for synergy is 24800) to the correct ip to get it to connect properly.

---

