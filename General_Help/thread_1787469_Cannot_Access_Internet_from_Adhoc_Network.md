---
title: "Cannot Access Internet from Adhoc Network"
date: 2011-06-21
forum: General Help
---

### Post by ankit.vader on 2011-06-21
I've a laptop which is connected to ethernet. I want to access internet from my N900 through wifi( available on Laptop). So i created adhoc network on laptop and connected my smart phone to it. But i still cannot access Internet from my phone. Where am I going wrong?? or is there another way to acces internet from my phone via laptop?

PS: I followed the procedure given in [this]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") link to create an adhoc network.

---

### Post by grahammechanical on 2011-06-21
I think that you need to set the laptop as a wireless Access Point (AP mode) and not Ad-hoc or Infrastructure mode.

I am basing this answer on information in my motherboard user guide. The motherboard has a built in Wireless adapter that can be used in one of three modes. Access Point, Ad-hoc and Infrastructure mode. This is done through the operating system. The motherboard maker has provided a Windows utility to set this up but not a Linux utility. Sadly, the Ubuntu Network Manger utility will allow you to set the mode to Ad-hoc or Infrastructure but not Access Point mode.

Here are links that may help you:

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)


[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

I suggest that you research Access Point mode in Linux or Ubuntu and also Bridging. I think that you need to create some sort of communication bridge between the ethernet adapter in the laptop that is connected to the Internet and the wireless adapter in the laptop that the mobile phone is connecting to.

I know that this information is not much help but it will set you in the right direction.

Regards.

---

