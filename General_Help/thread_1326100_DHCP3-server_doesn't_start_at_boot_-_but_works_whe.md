---
title: "DHCP3-server doesn't start at boot - but works when started afterwards"
date: 2009-11-14
forum: General Help
---

### Post by destrodk on 2009-11-14
Hello,

Have setup a Ubuntu 9.10 server, and installed and configured dhcp3-server. Everything works as expected.

Then I want to bridge one of the interfaces, so I can install openvpn, and suddenly dhcp3-server will not start at boot.

The config is as follows:

interfaces:
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.100.10
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto eth1
iface eth1 inet dhcp

When booting, I get: No subnet declaration for br0 (0.0.0.0) in the syslog. After boot, I can do a /etc/init.d/dhcp-server restart and it works.

I have googled and googled but can not find any answer.

Please help me :-)

Best regards

Henrik

---

### Post by jnorthr on 2009-11-14
wonder if this is a timing issue where the dhcp needs to have time to run before your other app start. If it starts b 4 dhcp, it may be grabbing some port dhcp needs. Just a gues, though... sorry.

---

### Post by destrodk on 2009-11-14
Hmm.. I'm not quite sure what you mean, but my guess is also, that it is some kind of timing problem. I have tried changing the rc2.d symlink for the dhcp server to s98 without luck.

Is there some pretty way to make it start 5 or 10 seconds after everything has started?

Since the server should not be rebooted often, I can restart dhcp service each time, but it is not a pretty solution :)

Thanks for the reply!

Henrik

---

### Post by mule007 on 2009-11-30
I'm having the exact same problem with a nearly identical network setup.

dhcpd does in fact appear to be attempting to run before the network interfaces have fully configured, and I suspect it may be due to the fact that there is a 10 second delay while configuring the bridge, during which time dhcpd attempts to load, does not discover any interfaces with addresses it can use, and fails.

I'm tempted to add a 30 second sleep to the init script for dhcpd, but would prefer a more graceful solution if anyone has any to offer.

---

### Post by pez252 on 2009-12-19
I have the same problem. I was adding wifi to my ubuntu router, and ran into this issue early on. At this point I'd changed samba, dhcpd, and my firewall script to point to br0 rather than eth1 (my internal wired interface).

Here are some log message that I think are related...
```
Dec 19 11:45:47 miniwall kernel: [   11.054150] Bridge firewalling registered
Dec 19 11:45:47 miniwall kernel: [   11.205679] device eth1 entered promiscuous mode
Dec 19 11:45:47 miniwall kernel: [   11.207812] r8169: eth1: link up
Dec 19 11:45:47 miniwall kernel: [   11.211796] device wlan0 entered promiscuous mode
Dec 19 11:45:47 miniwall kernel: [   11.253455] br0: port 1(eth1) entering learning state
Dec 19 11:46:02 miniwall kernel: [   26.252117] br0: port 1(eth1) entering forwarding state
```
I think the key point is the delay before entering the forwarding state.

If I disable the bridge and set dhcpd to listen on eth1 it works again at boot.

Edit:I went the easy route for fixing it until someone has a better idea... I added sleep to the start directive of the init script for dhcpd

---

