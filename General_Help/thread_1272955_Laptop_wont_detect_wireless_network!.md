---
title: "Laptop wont detect wireless network!"
date: 2009-09-22
forum: General Help
---

### Post by zking on 2009-09-22
I just installed Ubuntu 9.04 on my laptop. 

It's a HP Pavilion ze5500

For some reason, it wont detect a wireless network. I know I have one, it just wont detect it. 

I have no idea what to do. Please help :confused:

Thanks,

---

### Post by tgeer43 on 2009-09-22
You really don't give any information to go on but your notebook most likely has a wireless network adapter based on the Broadcom BCM43xx chipset. You can verify this by typing:
```
lspci
```in a terminal and looking for any lines which reference your network adapter. If it is indeed a BCM43xx based adapter then here are two links to official Ubuntu documentation that illustrate two completely different approaches to getting your wireless up and running.

The first method is the preferable one and should be tried first. It uses native Linux drivers but requires proprietary firmware which is not provided by Ubuntu. This is most likely why you are having problems. Here's the link:

[COLOR=Blue]_[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)_[/COLOR]

The second method is more involved and uses ndiswrapper with Windows drivers. Instructions can be found here:

[COLOR=Blue]_[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55)_[/COLOR]

If neither of these work for you then post back with the model of your network adapter and the exact nature of your problem.

tgeer

---

