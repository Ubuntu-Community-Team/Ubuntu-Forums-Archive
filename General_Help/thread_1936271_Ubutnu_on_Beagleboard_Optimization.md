---
title: "Ubutnu on Beagleboard Optimization"
date: 2012-03-05
forum: General Help
---

### Post by spizzak on 2012-03-05
Hi all, first post here so hopefully I'm putting this in the right place. Here's the situation:

I'm running ubuntu 11.10 on a beagleboard and doing some image processing from a webcam with OpenCV with a C++ app I have written. It works well on the laptop it was developed on but it's a bit slow on the beagleboard so I'm trying to optimize things so it'll run smoother. I would also like to optimize the boot time of Ubuntu on the BB as well. 

As of right now I've only disabled the 60 second search for a network like so:


root@omap:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE


My question is what are the major things I can do? Right now I'm thinking disabling the GUI/HDMI out would be a big help so what's the best way to do that? Right now I'm logging in over a serial connection so I'm not using any video output of the BB.

Also, is it possible to disable the network manager entirely or any other services that I most likely wont need to help speed up the boot process?

Maybe I should try running a lighter version of ubuntu altogther? Any help would be much appreciated.

Thanks!

---

