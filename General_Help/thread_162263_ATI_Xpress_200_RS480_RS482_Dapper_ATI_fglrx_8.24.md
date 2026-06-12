---
title: "ATI Xpress 200 RS480 RS482 Dapper ATI fglrx 8.24"
date: 2006-04-18
forum: General Help
---

### Post by mjziegle on 2006-04-18
Has anyone gotten the ATI Xpress 200 graphics to work with any version of Ubuntu? I have an MSI RS482-IL with an integrated Xpress 200 that always wants to use the mesa3d driver.

This particular "card" should be popular in recent budget laptops and budget motherboards based on the ati RS480/RS482 series chipsets.  It is _not_ the same thing as x300

If you have had sucess please post output from
 
1) lspci -v 
2) lspci -n
3) fglrxinfo
4) cat /var/log/Xorg.0.log | grep dri 
5) cat /var/log/Xorg.0.log | grep fglrx
5) xorg.conf (device and modules sections)

as well as any particular installation steps you had to perform.

I'm thinking only a small portion of the device IDs are actually supported which are particular to your motherboard or laptop.  

Thanks,

Matt

---

### Post by mystictim on 2006-04-23
Hi Matt,
I had the same problem with the latest version of Dapper Drake beta. It was driving me mad I followed all the instructions at [http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu") and at various locations on this forum. Then I read some where that I needed to remove the packages then reinsall them. Everything appears to work fine after I did the following:
> apt-get remove xorg-driver-fglrx
apt-get remove linux-restricted-modules-$(uname -r)
Then reinstalled and configured Xorg
> apt-get install linux-restricted-modules-$(uname -r)
apt-get install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg


Tim

---

