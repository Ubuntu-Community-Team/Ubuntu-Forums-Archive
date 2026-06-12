---
title: "UFW - NAT , forwarding and rules. I'm lost."
date: 2012-08-14
forum: General Help
---

### Post by legoyoda on 2012-08-14
Good morning everyone,

I am hoping you can help me out here.  I've been trying to get something done in Ubuntu using UFW and I've got myself lost and a bit confused. I'm trying to learn how to use ubuntu as a frewall and I have hit a wall.  I'm not super proficient with Lunix but have been using this as a learning exercise.

I am trying to achieve the following.

I have an ubuntu set as a firewall device with three NICs
     eth0 - 10.144.20.152 (internal network)
     eth1 - 192.168.20.100 (the external "RED" interface)
     eth2 - 192.168.30.100 (the DMZ "orange" interface)

Client commputer wise we have:
     computer 1 - 192.168.20.50 - this is the "outside computer"
     computer 2 - 192.168.30.50 - and "internal" computer 
     computer 3 - 192.168.30.75 - an FTP server

I'm trying to get it so that the system 192.168.20.50 can point an rdp or FTP request at 192.168.20.100 and then the firewall will NAT this request to the relevant system on the other network

Reading documentation I have edited /etc/default/ufw to have the "DEFAULT_FORWARD_POLICY=ACCEPT" and I've also added in the following lines to /etc/ufw/before.rules

-A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to-destination 192.168.30.50:3389
-A PREROUTING -i eth1 -p udp --dport 3389 -j DNAT --to-destination 192.168.30.50:3389
-A PREROUTING -i eth1 -p tcp --dport 21 -j DNAT --to-destination 192.168.30.75:21
-A PREROUTING -i eth1 -p udp --dport 21 -j DNAT --to-destination 192.168.30.75:21

I was under the impression that this would mean that anything incoming on eth1 (192.168.20.100) would be NAT'd over to the other network.  whilst this is the case (and I can RDP through) it allows the client to SPECIFICALLY go direct to the internal servers (192.168.30.50 and 192.168.30.75).  

I need to block direct requests to these servers and only allow RDP and FTP requests if it came from 20.100.  I.e. i want to mask the "internal" network from outside users.

It's at this point I got completely lost.  I switched the default_Forward_Policy to "drop" and this means i can ONLY directly reference the internal computers by .50 and .75 (whereas with the default_forward_policy set to accept all requests to .100 would successfully translate.

ufw is active and set to deny by default (except SSH)

Apologies if this seems complicated but I'm getting muddled up in what I actually wan to DO.. CAN I do this?

Any pointers appreciated Thanks

Alec

---

