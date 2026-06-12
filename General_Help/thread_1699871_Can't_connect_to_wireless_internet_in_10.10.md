---
title: "Can't connect to wireless internet in 10.10"
date: 2011-03-04
forum: General Help
---

### Post by studdard on 2011-03-04
Hi 

I have a 10.10 installation through Wubi. 

I can't connect to my wireless network.

I use the icon in the top right to try to connect but there does not seem to be a utility that searches for connections, or if there is it is not doing anything. Instead it seems that I need to set up the connection manually. I put in the SSID from the router, though I was never asked for this info in windows, but it wants my MAC address, which I can't find on the router. It also doesn't automatically ask for my wireless key which seems very strange; it only asks for it if I select WPA2 from a drop down menu. 

The ubuntu official guide on this told be to go into hardware drivers and enable proprietary drivers. There's no such thing but there is "additional drivers" and when I go into this it says there aren't any.

I'm stuck and require help. 

As an aside I've had a funny experienc with Ubuntu. I installed it on my laptop and thought it was great. Everything worked fine, connecting to the internet seemed to happen almost instantly just by putting in the wireless key, and I was thoroughly impressed. However, since I've installed 10.10 on my desktop through Wubi I've had nothing but problems. I can't even play media from my external hard drive. I don't know if it is appropriate to relate such experiences in this forum but I though I would.

Thanks for helping me.

---

### Post by wiggly81 on 2011-03-04
before we could help we would need to know the Wi-Fi Adapter in your computer, is it USB or PCI?
you can get a list of devices using these commands in terminal..
For PCI Devices
```
lspci
```
For USB Devices
```
lsusb
```

please run the relevent command and post the results in code tags using the "#" button on the reply form

---

### Post by grahammechanical on 2011-03-04
First, you are running Ubuntu inside windows. Windows is controlling the hardware. Ubuntu is accessing the hardware through Windows. So, I ask, is the wireless adapter switched on in Windows?

You say

>  there does not seem to be a utility that searches for connections,

There is but is is not activated if you do not have any network adapters (wired or wireless) in your machine. You do have these but Ubuntu does not detect them otherwise you will see a network icon with a red exclamation mark against it informing you that it is not connected either by wire or by wireless.

Do you see such an icon? You do not tell us.

You say

> It also doesn't automatically ask for my wireless key which seems very  strange; it only asks for it if I select WPA2 from a drop down menu. 

You do not need a wireless key if the connection is not encrypted but is open or unsecured. The network manager does not ask for a wireless key until you select an encrypted method of connection. Then, it will ask for the key. This is not strange by any means.

Wubi is running like any other Windows program. For it is a Windows program. If there are problems then the problems relate to how Wubi is configured not Ubuntu as you have found when you used Ubuntu on the laptop. Do you need to give Wubi access to the external drive in some Windows configuration setting?

Regards.

---

