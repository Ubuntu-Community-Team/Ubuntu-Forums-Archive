---
title: "Question about DHCPd"
date: 2012-04-02
forum: General Help
---

### Post by rockballad on 2012-04-02
Hello,

Could you please be kind enough to tell me something about DHCP?
I'm setting up a model of server-client on LAN, a cloud indeed. The client will request the server to boot one or many virtual machines (VMs). The server has DHCP installed. So, every VM which has been launched will be assigned an IP.

My question is, how about the IP of those VMs? E.g. my LAN configuration is:
- gateway 192.168.0.1
- server: 192.168.0.10
- client: 192.168.0.20

I don't know how to configure the DHCP. What is the relation of this DHCP (of the server node) with the DHCP of the router that is managing the whole LAN (client, server, others...). Is it true that we will have 2 DHCP servers? Otherwise, if the DHCP of the server node shares the network with the current DHCP, all VM will have IP 192.168.0.x?

So, to make thing simple, what following configuration will be OK?

1/ DHCP of server will manage and assign IPs of 192.168.1.x
2/ DHCP of server will share the current IPs of 192.168.0.x

What I'm confused is the co-existence of DHCPs. Usually, we have a default DHCP, maybe at router level, so it can assign IPs to all machines on LAN. That's why my server is 192.168.0.10, client is 192.168.0.20. Now, if I setup a new DHCP server, what it looks like? Share the current IP ranges, or create a new one? What is its role on my LAN? 

I hope you can help me out. Thank you so much!

---

### Post by btindie on 2012-04-02
If you're using KVM, and other ones I guess, it'll create a virtual network interface on your server and have it (dnsmasq) bind to only that interface so it does cause a problem with external DHCP servers.

You won't be able to externally access your VM's as by default they're configured for a routed network. If your ADSL router supports additional routes, you can add a static route on that to your server for your VM network range that KVM assigns. Or you could add it directly on your client machine which would be the easiest if it's just a one off.

The other alternative is to do port forwarding on your server so it would say map
192.168.0.10:80 -> 192.168.123.50:80
If you were to give your server multiple STATIC private addresses you could forward the same port, e.g. 80, to different hosts using multiple IP's. Where as by using a DHCP acquired address you're limiting yourself plus you can't then run anything on that server on the same port.

A way around that and possibly simpler option is to just create a bridge interface so it ends up getting IP's from your ADSL router.

[http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging](http://wiki.libvirt.org/page/Networking#Debian.2FUbuntu_Bridging)
[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-10.10)

---

### Post by rockballad on 2012-04-02
Thank you so much, btindie. I find something clearer now. I'll investigate more from you links.

For now, I just add that I created a bridge on the client node, br0 (that links to eth0). So, every VM I create directly (by virsh for example, yes, KVM), it is configured properly and connects to Internet just fine (with br0).

But now, with a server node with DHCPd installed, in order to give public and private IPs to VMs that manage, I'm not sure how to configure that DHCP server. For example, can I use my current gateway as DNS of that DHCP? Sorry maybe i'm wrong as I'm not sure.

Once the VM booted, I think it also stays on my LAN, so it should have IP of 192.168.0.x, same subnet as others. 

I'll reply once more later. Thanks again!

---

### Post by simitchdar on 2012-04-02
Takks!Dette er et stort behov for!

---

### Post by rockballad on 2012-04-17
I solved it. I really don't understand the role of each element much, but this is the way I did:
- install dhcp3-server on the server node.
- modify dhcp3.conf file, to use router IP as "option routers"
- edit the range, etc, as usual
- include the dhcp.entries file in which it specifies the IP, MAC addr...

---

