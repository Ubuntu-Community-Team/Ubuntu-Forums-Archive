---
title: "EtherChannel bonding against a Cisco Catalyst switch?"
date: 2011-10-25
forum: General Help
---

### Post by k999 on 2011-10-25
Hi,

I have a Cisco Catalyst switch with 1Gbit ports, but it has a 10Gbit uplink. I'd like to bond 2 1Gbit ethernet from my workstation to the switch (EtherChannel), so that I get higher transfer rates. It's possible, here's an example for RedHat EL:

[http://zmq503o1.wordpress.com/2008/11/19/linux-etherchannel-double-your-pleasure-double-your-fun/](http://zmq503o1.wordpress.com/2008/11/19/linux-etherchannel-double-your-pleasure-double-your-fun/)

It's even possible in Windows:

[http://www.cisco.com/en/US/tech/tk389/tk213/technologies_configuration_example09186a008089a821.shtml](http://www.cisco.com/en/US/tech/tk389/tk213/technologies_configuration_example09186a008089a821.shtml)

But what's the "right" way to do this on Ubuntu? With NetworkManager taking over, I have to admit I no longer know what's the right way to take control of the network interfaces without screwing anything up... Not that I've tried yet. Perhaps I should just remove NetworkManager and set things up manually, as suggested by:

[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

---

### Post by Gyokuro on 2011-10-25
Hi,

you can disable the Network Manager service and configure your bonding device - it's not necessary to uninstall the Network Manager. Afterwards configure your channel bonding device described like in your mentioned link.

---

### Post by k999 on 2011-10-25
Thanks, I'll give that a go.

By the way, you wouldn't happen to know why [DHCP-client triggers have stopped working in Ubuntu 11.*]("http://ubuntuforums.org/showthread.php?t=1868341") as well? :)

---

