---
title: "How to enable ethernet interface only (without IP or any other configuration)"
date: 2011-05-15
forum: General Help
---

### Post by shadowwyvernx on 2011-05-15
Hello,

Quick background: After reading of people virtualizing their firewall appliances, I have been inspired to try doing the same.  I have an Ubuntu Server system that I will be using as a host.  It will have 2 NICs - one connects to the LAN, and the second I will be adding will connect to the WAN (in this case, the real internet).  Both adapters will have bridged networking to the firewall VM (in this case pfsense, but my question is centered around configuring the host not the guest) - so the VM will be able to interact with the LAN through the server interface, and be able to see the internet from the other NIC.

Ok, so I guess that was more than just background :) Anyway:

I want to run a VM and essentially dedicate a NIC to it using bridged networking.  This NIC will connect without a firewall to the internet, so it is essential that the host *not* send or be able to receive any traffic on it.  I assume, though, in order for bridged networking to work the host needs to at least have the NIC brought up.  How do I configure it so that it is impossible for the host to communicate through that interface?  Is it sufficient just to delete any configuration information from /etc/network/interfaces?  I don't want anything going out that interface - indeed to avoid possibly confusing the modem on the other end, there should *never* be any ethernet frames emitted from the interface with the MAC address of the host.  To be clear, the host does not need this NIC for anything; if I could directly give the hardware to the guest (can I?) I would...

I'm not committed to this particular configuration, only the end result, so if someone knows of a better way to accomplish the same thing (the host not being able to send ethernet frames over that interface at any time), I'd be grateful to hear it.  I know I don't have as much control over receive, but if there is a way to drop all ethernet frames on the host, that would be important too.  Again, the objective is to turn the interface from the hosts perspective into a black hole, while letting the guest that is bridged to that interface operate normally.

Thanks!

---

