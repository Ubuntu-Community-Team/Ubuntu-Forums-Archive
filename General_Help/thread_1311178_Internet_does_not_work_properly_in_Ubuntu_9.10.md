---
title: "Internet does not work properly in Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by Rimdeker on 2009-11-02
Hey guys, I got a little problem. My internet does not work properly on Ubuntu 9.10. Everytime I boot up my PC I have to unplug my modem and plug it in after my desktop loaded up completely. Then I have to use pppoeconf again to connect to the internet, pon dsl-provider does not work.
My Motherboard: MSI DKA790GX
I'm using a DSL connection using a modem.

When it connects succesfully:
> 
CHAP authentication succeeded: access accepted : ar2548887147
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: CHAP authentication succeeded
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: peer from calling number 00:30:88:01:66:72 authorized
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: Cannot determine ethernet address for proxy ARP
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: local  IP address 84.60.198.73
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: remote IP address 84.60.192.1
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: primary   DNS address 195.50.140.178
Nov  2 15:28:35 rimdeker-desktop pppd[4623]: secondary DNS address 195.50.140.114


When I type pon dsl-provider without unplugging my modem during boot-up I get and the internet does not work:
> 
root@rimdeker-desktop:/home/rimdeker# pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
root@rimdeker-desktop:/home/rimdeker# plog
Nov  2 16:05:13 rimdeker-desktop pppd[4353]: Plugin rp-pppoe.so loaded.
Nov  2 16:05:13 rimdeker-desktop pppd[4353]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Nov  2 16:05:13 rimdeker-desktop pppd[4355]: pppd 2.4.5 started by root, uid 0



then I go throuhg the ppoeconf I get:
> 
root@rimdeker-desktop:/home/rimdeker# plog
Nov  2 16:05:48 rimdeker-desktop pppd[4355]: Timeout waiting for PADS packets
Nov  2 16:05:48 rimdeker-desktop pppd[4355]: Unable to complete PPPoE Discovery
Nov  2 16:06:53 rimdeker-desktop pppd[4355]: Timeout waiting for PADS packets
Nov  2 16:06:53 rimdeker-desktop pppd[4355]: Unable to complete PPPoE Discovery
Nov  2 16:07:58 rimdeker-desktop pppd[4355]: Timeout waiting for PADS packets
Nov  2 16:07:58 rimdeker-desktop pppd[4355]: Unable to complete PPPoE Discovery
Nov  2 16:08:34 rimdeker-desktop pppd[4605]: Plugin rp-pppoe.so loaded.
Nov  2 16:08:34 rimdeker-desktop pppd[4605]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Nov  2 16:08:34 rimdeker-desktop pppd[4607]: pppd 2.4.5 started by root, uid 0


By the way, pppoeconf tells me that I got two hardware:
eth0
vboxnet0


Does anybody know a solution for this little uncomfourtable problem?

---

