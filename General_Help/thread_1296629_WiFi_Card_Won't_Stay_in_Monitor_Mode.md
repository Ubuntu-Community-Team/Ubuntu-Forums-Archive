---
title: "WiFi Card Won't Stay in Monitor Mode"
date: 2009-10-20
forum: General Help
---

### Post by ld.4lpha on 2009-10-20
I put my card into monitor mode, and then when I bring the interface back up and it connects to my AP, it automatically reverts to managed mode. :mad:

Thoughts?

```
ld4lpha@makalu:~$ sudo ifconfig wlan0 down
ld4lpha@makalu:~$ sudo iwconfig wlan0 mode monitor
ld4lpha@makalu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

ld4lpha@makalu:~$ sudo ifconfig wlan0 up
ld4lpha@makalu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"myESSID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: aa:bb:cc:dd:ee:ff   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Cuddles McKitten on 2009-10-20
I could be wrong, but isn't the whole point of monitor mode that you're not connected to an AP and can just capture any packets floating around?  I think the ifconfig wlan0 up is unnecessary for doing anything in monitor mode.

---

### Post by ld.4lpha on 2009-10-20
My understanding is that monitor mode is used to capture packets intended for all devices in the vicinity...not just my device.

<edit>

I should clarify...

I may want to capture all packets on a network that I'm connected to regardless of whether that packet is sent to my machine.

Regarding not bringing the interface up, isn't an active interface necessary to capture anything regardless of monitor mode or managed mode?

</edit>

---

### Post by Niko Johnson on 2009-10-20
try this method ```
 airmon-ng start wlan0 
``` if you dont have airmon just do a quick apt-get to install it

---

### Post by Cuddles McKitten on 2009-10-20
> **ld.4lpha said:**
> 
I should clarify...

I may want to capture all packets on a network that I'm connected to regardless of whether that packet is sent to my machine.

Regarding not bringing the interface up, isn't an active interface necessary to capture anything regardless of monitor mode or managed mode?

</edit>

That's promiscuous mode you're describing.  You can get that from running any decent packet sniffer.

---

### Post by ld.4lpha on 2009-10-20
> **Niko Johnson said:**
> try this method ```
 airmon-ng start wlan0 
``` if you dont have airmon just do a quick apt-get to install it

Duh.  I should have known that.

Thanks!

> **Cuddles McKitten said:**
> That's promiscuous mode you're describing. You can get that from running any decent packet sniffer.

You are right.  The difference, I believe, is that monitor mode can operate connected to an AP or not connected to an AP.

Promisc mode requires that you be connected to a network.  Hence, it is typically used on a wired network.

---

### Post by Niko Johnson on 2009-10-20
haha it happends to the best of us.. glade i can help

---

