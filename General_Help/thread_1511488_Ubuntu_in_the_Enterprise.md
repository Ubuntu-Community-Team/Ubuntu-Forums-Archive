---
title: "Ubuntu in the Enterprise"
date: 2010-06-16
forum: General Help
---

### Post by packetman255 on 2010-06-16
So I've been using FreeBSD since 1996 and have about a dozen Fedora boxes in production in a large enterprise (6,000 to 7,000 users).  Now I'm looking at Ubuntu as a possible desktop OS replacement.  We will soon be starting a pilot project.  I have a couple of workstations setup and use these daily but there are two things I think that will get this shot down very quickly.

1. Centralized Patch and Package management.  If I want to push a set of patches out to groups of machines (think Microsoft SMS).

2. Is there anything similar to netbios or apple talk where machines discover each other so you can see a list of all machines on a subnet.

Also, is OpenVPN considered the one of the best/better VPN clients?  And when I ask that question I'm asking from the standpoint of gui tools to setup and manage it.  While I'm very comfortable at the command line.  This whole project will rock a lot of peoples worlds.

---

### Post by Chesamo on 2010-06-16
> **packetman255 said:**
> 1. Centralized Patch and Package management.  If I want to push a set of patches out to groups of machines (think Microsoft SMS).
You can create your own internal repository if you like.
> **packetman255 said:**
> 2. Is there anything similar to netbios or apple talk where machines discover each other so you can see a list of all machines on a subnet.
I believe Ubuntu installs default to network discovery; I could be wrong about that.

I'm not familiar with the inner workings of OpenVPN, so I can't really help you there.

---

### Post by amauk on 2010-06-16
1)
If you're catering for many users,
you may want to investigate booting machines over the network (via LTSP)
Often called "fat clients"

Your server will store a compressed OS image (or more than one, if you wish)
and client machines, when switched on, boot off of this image

Unlike the "thin client" model, where clients are just dumb terminals, this fully utilises the hardware on client machines
it's just that they are not booting from local storage

Doing this, means you only have a single OS image to administer, and it's stored on the server (so no going around to people's desks)

Drawbacks,
your network is now an essential part of client operations
network down, no-one can use any machines

2)
depends what you're trying to do
just a simple ping of the subnet will bring back all machines
Why do you need machines to know about each other?

---

### Post by packetman255 on 2010-06-16
> **amauk said:**
> 1)
If you're catering for many users,
you may want to investigate booting machines over the network (via LTSP)
Often called "fat clients"

Your server will store a compressed OS image (or more than one, if you wish)
and client machines, when switched on, boot off of this image

Unlike the "thin client" model, where clients are just dumb terminals, this fully utilises the hardware on client machines
it's just that they are not booting from local storage

Doing this, means you only have a single OS image to administer, and it's stored on the server (so no going around to people's desks)

Drawbacks,
your network is now an essential part of client operations
network down, no-one can use any machines


This is very interesting concept.  Not worried about the network being down for the most part.  We run call centers and utilize VOIP so if the networks down they aren't taking calls and I have other issues to deal with...

> 
2)
depends what you're trying to do
just a simple ping of the subnet will bring back all machines
Why do you need machines to know about each other?

Well I don't necessarily need all the machines to know about each other.  I guess what I need is the user to know the workstation name so we could possibly RDP to it for remote support.  So basically to answer my own question, if DNS is working properly that will take care of itself.

---

### Post by prodigy_ on 2010-06-16
Samba (nmbd) allows you to use NetBIOS names as if you were running Windows. You can set up a WINS server also.

Or, if you prefer DNS, dhclient can register hostnames there (**send host-name** option in dhclient.conf).

---

### Post by alphacrucis2 on 2010-06-17
We use OpenVPN here even for Windows PC's. It's configured to use in house generated user certificates for authentication. Works very well. You can also use netfilter on the OpenVPN server to control what remote users can connect to.

---

### Post by Chesamo on 2010-06-17
> **packetman255 said:**
> Well I don't necessarily need all the machines to know about each other.  I guess what I need is the user to know the workstation name so we could possibly RDP to it for remote support.  So basically to answer my own question, if DNS is working properly that will take care of itself.
Ubuntu doesn't use RDP; it uses VNC.

---

### Post by amauk on 2010-06-17
> **packetman255 said:**
> This is very interesting concept.  Not worried about the network being down for the most part.  We run call centers and utilize VOIP so if the networks down they aren't taking calls and I have other issues to deal with...
Exactly,
for most network setups, clients are pretty much useless on their own anyway

Some docs about LTSP

Ubuntu LTSP wiki page
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Page about Fat Clients
[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

> **Chesamo said:**
> Ubuntu doesn't use RDP; it uses VNC.
You can use RDP
there's an open source client called rdesktop
(I believe it's even included in Ubuntu by default?)

Anyway, wikipedia page here
[http://en.wikipedia.org/wiki/Rdesktop](http://en.wikipedia.org/wiki/Rdesktop)

As you can see, the majority of RDP features are implemented, but some aren't (probably due to patent / licensing issues, although I'm just guessing)

---

### Post by Chesamo on 2010-06-17
> **amauk said:**
> You can use RDP
there's an open source client called rdesktop
No, not client. Server. Ubuntu does not use RDP to serve to the client machine. It uses VNC.

---

