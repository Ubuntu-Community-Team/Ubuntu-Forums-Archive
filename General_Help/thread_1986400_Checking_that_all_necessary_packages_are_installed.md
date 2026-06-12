---
title: "Checking that all necessary packages are installed"
date: 2012-05-24
forum: General Help
---

### Post by wizzor on 2012-05-24
Hi all,
I have a somewhat weird problem.

I upgraded to 12.04 from 11.10 normally, but it seems not all packages were installed properly. This is weird. I found this out because I started getting complaints not all updates can be installed, and turned out some packages were missing. Most notably the network-manager applet was completely missing.
This still seems to produce some fallout, as for example the "More networks" submenu in wireless doesn't seem to ever contain anything. Also, using the applet often leads to a crash of gnome-control-center. I suspect this is due to another missing package too, but cannot tell which.
How can I check which packages are missing? 
I tried
```
sudo apt-get check 
```
doesn't seem to show anything as missing.

Could there be other reasons for this strange behavior?

---

