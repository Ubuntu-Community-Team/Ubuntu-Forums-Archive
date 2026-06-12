---
title: "Network issues after kernel update."
date: 2010-09-19
forum: General Help
---

### Post by HPD2 on 2010-09-19
Since updating to the 2.6.32-24.43 kernel I am unable to connect to the network. Its like the networking was disabled, but its not. I wasn't even able to access my router on the network. Every thing works fine in my earlier kernel, I'm using that for the time being.

---

### Post by afrowildo on 2010-09-20
You could try reporting it as a bug? It may be that you just have to wait for a fix to be released.

[https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies)

---

### Post by slakkie on 2010-09-20
Try installing the kernel headers, eg: aptitude install linux-headers-generic if you have a generic kernel.

Otherwise, lshw -C network

```


sudo lshw -C network
[sudo] password for wesleys: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:b1:66:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.1.9 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:f6cff000-f6cfffff

```

You see the driver, now search to see which package has that driver:

```

apt-file search iwl3945

```

and that will hopefully give you some packages which include the correct driver..

Best of luck.

---

### Post by HPD2 on 2010-09-20
I decided to boot into the newer kernel to try to get things working, and when I checked I was connected. I think the sky2 driver was just being wonky for what ever reason. Thanks for the help though.

---

