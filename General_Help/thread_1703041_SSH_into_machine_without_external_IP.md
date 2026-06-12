---
title: "SSH into machine without external IP"
date: 2011-03-08
forum: General Help
---

### Post by WeebleMonkey on 2011-03-08
Hi,

I have two machines sitting in different offices. 

Machine A is an ubuntu server box which *does not* have an external IP address, but is connected to the internet.

Machine B is an ubuntu server box which *does* have an external IP address (and is connected to the internet).

As it stands, machine B cannot ssh into machine A, only the other way around. What I was wondering is is it possible for machine A to setup some sort of tunnel which machine B can then use to connect back to machine A? I only need SSH access, and I only need it from Machine B to Machine A.

Any help on this matter is very much appreciated,
Thank you.

---

### Post by lithopsian on 2011-03-08
Every machine on your network will have an IP address, possibly only an internal one.  It may also be different every time you login to the network, although it is possible to bind a static IP to each machine.  Internal network addresses are typically of the form 192.168.0.X.  Then you can ssh to the machine, assuming it has the necessary ssh server software and is configured to let you in.

---

### Post by pricetech on 2011-03-08
Are you able to configure, or have configured for you, port forwarding on "router a" ??

---

### Post by WeebleMonkey on 2011-03-08
Looks like I have managed to solve most of the problem:

```

MachineA: autossh user@MachineB -R 8022:localhost:22 -f -N
MachineB: ssh user@localhost -p 8022

```

The only problem now is that if MachineB restarts, then autossh seems to think it shouldn't reconnect. (It only reconnects if there is an error).

---

### Post by WeebleMonkey on 2011-03-08
Thanks for your help lithospan & pricetech. 

I should have mentioned that I don't want MachineA to have an external IP. MachineA is just a normal internal server on the network at OfficeA and MachineB is a dmz server at OfficeB.
Opening up MachineA with a public IP & routing ports to it normally would require far to much work both from a firewall point of view and from an internal office politics point of view.

---

