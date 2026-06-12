---
title: "Classification of bug affecting all network connections?"
date: 2010-07-23
forum: General Help
---

### Post by Taemojitsu on 2010-07-23
This bug was reported in the [networking and wireless](http://ubuntuforums.org/showthread.php?p=9584971#post9584971) forum and as a package-less bug on [launchpad](https://bugs.launchpad.net/ubuntu/+bug/605148) ([reposted](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/609348) in 'linux' package), but neither of those got a response. Where would be the correct package to report this bug to so it can be fixed?

It is not wireless-related, but general to all network (or maybe just IP) connections regardless of the hardware interface.


Description of bug:

If too much information is sent to an unresponsive network connection, the connection seems to 'fail' and stops working. The unresponsive network connection is usually the result of a proxy or NAT router restarting.

Steps to duplicate in 10.04:

1) set up "ping -f google.com -i 10"
2) set up "ping -f google.com -i 1"
3) restart router

Result: the flood ping with interval 10 will show one or two dropped packets while the router is restarting, and then will show no further errors. The flood ping with interval 1 will continue to show dropped packets after the router has restarted, as too much information is in the connection buffer or something.

This also applies to IM connections (tested with Pidgin connected to MSN). If update information is sent while the router is restarting, the connection to the server 'stalls' and is only reset by the application after 15 minutes. If no information is sent while the router is restarting, the connection works fine immediately after the router has finished restarting and connected to ISP.


Also tested this on 10.04 32-bit from a Live usb. First test with 10-sec interval stalled when restarting router, but with a 20-sec interval, there was only one missed packet and then resumed normal operation. Meanwhile the 1-sec interval ping completely stalled even after the router finished restarting.

---

### Post by dcstar on 2010-07-24
> **Taemojitsu said:**
> This bug was reported in the [networking and wireless](http://ubuntuforums.org/showthread.php?p=9584971#post9584971) forum and as a package-less bug on [launchpad](https://bugs.launchpad.net/ubuntu/+bug/605148) ([reposted](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/609348) in 'linux' package), but neither of those got a response. Where would be the correct package to report this bug to so it can be fixed?

It is not wireless-related, but general to all network (or maybe just IP) connections regardless of the hardware interface.


Description of bug:

If too much information is sent to an unresponsive network connection, the connection seems to 'fail' and stops working. The unresponsive network connection is usually the result of a proxy or NAT router restarting.
........

That is not a bug, that is how the IP protocol was designed to operate.

If a network connection fails (as determined by various criteria) then the protocol looks for alternative routes to use. After a certain period the faulty route is tested to see if it is again available.

The IP network was designed to keep working even if specific routes between destinations failed, this is just an example of that mechanism - if you only have one route that is not 100% reliable then it tries to do the best it can.

---

