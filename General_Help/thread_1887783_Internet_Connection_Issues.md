---
title: "Internet Connection Issues"
date: 2011-11-27
forum: General Help
---

### Post by noobinabox on 2011-11-27
I am currently running Ubuntu 10.04

Internet works, but oftentimes, I lose connection to the internet, even though my computer claims I am connected to wifi. I have found a temporary, yet annoying, fix; I manually disable and re-enable wireless connections (disconnecting and reconnecting works as well). The fix is only temporary, as the problem may reoccur.

I have a windows partition on this same computer, and wireless internet works flawlessly.

What other information is relevant to diagnosing/solving this problem?
I believe my wireless card information would be relevant, but I'm not sure how to obtain this info.

Thanks guys,
Noobinabox

---

### Post by gman16000 on 2011-11-27
you can find your wireless hardware with this terminal command:
```
sudo lshw -C network
```

---

### Post by noobinabox on 2011-11-28
lshw -C network produces the following for the wireless interface:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:b1:94:0a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.32-35-generic firmware=8.24.2.12 ip=128.62.209.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff

```


iwconfig produces

```
wlan0     IEEE 802.11abgn  ESSID:"restricted.utexas.edu"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:23:EB:27:80:F1   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any advice?

---

