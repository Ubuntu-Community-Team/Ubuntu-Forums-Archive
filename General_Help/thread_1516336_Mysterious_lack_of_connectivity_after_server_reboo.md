---
title: "Mysterious lack of connectivity after server reboot"
date: 2010-06-23
forum: General Help
---

### Post by thk on 2010-06-23
Every time I reboot my server, it no longer connects to the internet. It is dual-homed with an internal and an external interface. Both come up. The internal connection works fine. Nothing happens on the external interface.

Ifconfig shows that both interfaces are setup correctly. My iptables settings are properly restored. Forwarding is automatically enabled. For some reason packets do not go anywhere on the external interface. This has been true ever since the upgrade to jaunty I think (now running lucid).

Once I restart the external interface it works perfectly (eg ifdown eth1; ifup eth1 or /etc/init.d/networking restart). The problem only occurs after a reboot and only occurs on the external interface.

Here's my /etc/network/interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.1.1
  netmask 255.255.255.0
  gateway 192.168.1.1

auto eth1
iface eth1 inet static
  address 129.116.71.233
  netmask 255.255.255.0
  gateway 129.116.71.129
  post-up iptables-restore < /etc/network/iptables
  post-up sysctl net.ipv4.ip_forward=1
  post-down sysctl net.ipv4.ip_forward=0

---

### Post by dcstar on 2010-06-24
> **thk said:**
> Every time I reboot my server, it no longer connects to the internet. It is dual-homed with an internal and an external interface. Both come up. The internal connection works fine. Nothing happens on the external interface.

Ifconfig shows that both interfaces are setup correctly. My iptables settings are properly restored. Forwarding is automatically enabled. For some reason packets do not go anywhere on the external interface. This has been true ever since the upgrade to jaunty I think (now running lucid).

Once I restart the external interface it works perfectly (eg ifdown eth1; ifup eth1 or /etc/init.d/networking restart). The problem only occurs after a reboot and only occurs on the external interface.
........

Make sure that things like network-manager are not installed, you may also want to put the restart command into /etc/rc.local.

---

