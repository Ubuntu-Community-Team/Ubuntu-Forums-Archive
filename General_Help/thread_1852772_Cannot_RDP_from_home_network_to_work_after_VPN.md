---
title: "Cannot RDP from home network to work after VPN"
date: 2011-09-30
forum: General Help
---

### Post by pablorpm on 2011-09-30
I posted an a thread a while ago but got no responses. I am still having trouble logging into my work desktop (Windows OS) from my home laptop (Ubuntu 11.04) from my home network. I am able to establish a successful VPN connection to my network but unsuccessful in remoting to work using Reminna Remote Desktop client.

I have narrowed it down to my router (D-Link 624) or Ubuntu issue. I am able to VPN and RDP using another computer (Win 7 OS) on my same home network. I connected my laptop directly to my modem using an ethernet cable and was successful in establishing VPN connection and RDP to my work computer.

I keep finding port forwarding solutions, but I don't think that applies to my case. So what am I missing?

Thanks in advance for any tips or advice!

---

### Post by dcstar on 2011-09-30
> **pablorpm said:**
> I posted an a thread a while ago but got no responses. I am still having trouble logging into my work desktop (Windows OS) from my home laptop (Ubuntu 11.04) from my home network. I am able to establish a successful VPN connection to my network but unsuccessful in remoting to work using Reminna Remote Desktop client.

I have narrowed it down to my router (D-Link 624) or Ubuntu issue. I am able to VPN and RDP using another computer (Win 7 OS) on my same home network. I connected my laptop directly to my modem using an ethernet cable and was successful in establishing VPN connection and RDP to my work computer.

I keep finding port forwarding solutions, but I don't think that applies to my case. So what am I missing?

Thanks in advance for any tips or advice!

Be aware that the latest RDP host protocol from Microsoft is not compatible with Linux RDP clients - you have to "dumb down" the settings on the RDP host to accept the earlier versions of RDP clients. Corporate PCs may be set to only use the more strict settings.

You also need to check that you can ping the remote PC once you have your VPN up, and also you may need to use its IP address instead of a name.

---

