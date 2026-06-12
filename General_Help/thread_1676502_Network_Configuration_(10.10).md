---
title: "Network Configuration (10.10)"
date: 2011-01-27
forum: General Help
---

### Post by FMDragon on 2011-01-27
Hey folks, I have a question about the network configuration GUI in Ubuntu 10.10.

This is the first time in a while that I've needed to set up a Ubuntu system with a static IP. The last time I had to manually enter the information into the /etc/network/interfaces file. But now, I see that a GUI has been added to allow this. My question, is there any syncing involved between the two processes? If I were to set the static IP using the GUI would it fill in the interfaces file? Do I need to do both on my own? How exactly would this work now?

Thanks in advance for any information you folks can give.

---

### Post by justleen on 2011-01-27
If you use the GUI (aka the networkmanager) you shouldnt touch the interfaces file. 
Anything in the interfaces file will be ignored, network manager uses its own config.

If you want to switch back to the "old" way with the interfaces file, you have to specify this to the networkmanager, by setting "managed=false/true" in  /etc/NetworkManager/nm-system-settings.conf

(Im writing false/true, cause Im not sure which one is "enable interfaces file" from my head)

---

### Post by FMDragon on 2011-01-27
Thanks for the information. Good to know how the two methods work together!

---

