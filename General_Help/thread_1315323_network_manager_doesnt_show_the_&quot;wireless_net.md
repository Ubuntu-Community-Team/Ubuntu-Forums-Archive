---
title: "network manager doesnt show the &quot;wireless networks&quot; option"
date: 2009-11-05
forum: General Help
---

### Post by bodyharvester on 2009-11-05
as the title says, when i left click on network manager it shows the wired networks (disconnected, there arent any), mobile broadband (what im using now) but it doesnt display the &quot;wireless networks&quot; which i can connect to on live CD (9.04)  im using 9.10 not 9.04 now  thanks

---

### Post by beastrace91 on 2009-11-05
You said you can see the networks using the Ubuntu 9.04 LiveCD can you see them using a 9.10 Live Disc? If not it sounds like perhaps your Wifi card is experiencing a regression with the latest Ubuntu release. What type of card do you have?

~Jeff

---

### Post by bodyharvester on 2009-11-05
hi, thanks for answering,   i cant see the wireless networks in 9.10 live cd either  the code sudo lshw -C network produced this  ```
description: Network controller        product: BCM4312 802.11b/g        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        version: 01        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list        configuration: latency=0        resources: memory:f0200000-f0203fff
```  i will be upgrading my wireless card in the near future i hope to an Intel 3945 ([http://www.amazon.co.uk/Intel-Wireless-3945ABG-Network-Connection/dp/B000F6IL6Y/ref=sr_1_1?ie=UTF8&s=electronics&qid=1257429881&sr=8-1](http://www.amazon.co.uk/Intel-Wireless-3945ABG-Network-Connection/dp/B000F6IL6Y/ref=sr_1_1?ie=UTF8&s=electronics&qid=1257429881&sr=8-1))  i hope that info helps  thanks again

---

### Post by Inkpot on 2009-11-05
I'm having the exact same problem. Jaunty detected my wifi network just fine, but since upgrading to Karmic, no wifi networks are detected. I'm dual-booting with Windows 7 and have no problems with windows detecting my wife network, either.

Any suggestions?

---

### Post by seenthelite on 2009-11-06
This sounds like the same problem I had immediately after the first boot after I installed 9.10. Wired was fine but wireless was not. Using Synaptic Package Manager I removed Network Manager and at the same time installed WICD. Then rebooted and WICD detected my AP and its been working fine ever since then, in fact better than Network Manager ever did in 9.04, wireless connects automatically by the time the boot finishes.

---

