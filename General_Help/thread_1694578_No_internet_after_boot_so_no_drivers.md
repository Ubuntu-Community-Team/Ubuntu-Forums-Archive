---
title: "No internet after boot so no drivers"
date: 2011-02-24
forum: General Help
---

### Post by Kr1 on 2011-02-24
I just installed the new version of ubuntu. But after install I found out I cant connect to the internet, so I cant install drivers.

My computer is an Acer Aspire 5920

What do I have to do too connect to the internet? Do I have to download the ethernet driver and install so I can download and install the others? And how do I install the driver? and where can I find it?

By the way, I am a total n00b on ubuntu.

Here are my specs:

Intel Core 2 Duo mobile processor T7300
Mobile Intel PM965 Express Chipset
Intel Wireless WiFi Link 4965AGN (dual-band quad-mode 802.11a/b/g/Draft-N)
Bluetooth 2.0+EDR
2 GB of DDR2 667 MHz memory, upgradeable to 4GB using two soDIMM modules (dual-channel support)
15.4" WXGA high-brightness (220-nit) Acer CrystalBrite TFT LCD, 1280 x 800 pixel resolution, 8 ms response time
NVIDIA GeForce 8600M GT with up to 1GB of TurboCache technology (256 MB of dedicated GDDR2 VRAM, up to 768 MB of shared system memory)
Dolby-certified surround sound system with two built-in stereo speakers and one subwoofer supporting low-frequency effects
160 GB hard disk drives
5-in-1 card reader
DVD Super Multi DL Optical Drive
Integrated Acer Crystal Eye webcam (0.3 megapixel)
364 (W) x 270.2 (D) x 30.8/43.7 (H) mm (14.3 x 10.6 x 1.2/1.7 inches) 3.00 kg (6.61 lbs.)
Included Accessories: Mouse, Travel bag, Power cord, Manual, Starter CD

---

### Post by marshag63 on 2011-02-24
Number one - don't panic  :)
Just for clarification, we are talking about a wireless connection right and not ethernet using a cable?

I have an acer aspire one, which has no problem with wifi.  What we need to determine is what chipset your wifi adapter is using.

In a terminal run the command "lspci" (without quotes) and post back what the output is.  (this is a command to list all PCI devices of the computer - it will give us the chipset ID so we can determine next step.

Please post output as above and also see here:  [http://linux-wless.passys.nl/query_part.php?brandname=Intel](http://linux-wless.passys.nl/query_part.php?brandname=Intel) (driver iwl4965).  Doing an "lsmod" and checking the output for "iwl4965" will show if the module is loaded is the next step.

MDG

---

### Post by Kr1 on 2011-02-24
> **marshag63 said:**
> Number one - don't panic  :)
Just for clarification, we are talking about a wireless connection right and not ethernet using a cable?

I have an acer aspire one, which has no problem with wifi.  What we need to determine is what chipset your wifi adapter is using.

In a terminal run the command "lspci" (without quotes) and post back what the output is.  (this is a command to list all PCI devices of the computer - it will give us the chipset ID so we can determine next step.

Please post output as above and also see here:  [http://linux-wless.passys.nl/query_part.php?brandname=Intel](http://linux-wless.passys.nl/query_part.php?brandname=Intel) (driver iwl4965).  Doing an "lsmod" and checking the output for "iwl4965" will show if the module is loaded is the next step.

MDG
Actully it is the internet with the cable, its not wi-fi, I can connect too wireless, but not with cable.

---

### Post by rhoparkour on 2011-02-25
In order to clarify, you have a working wireless connection?

If so, go to System > Administration > Drivers (or something like this)*.

Input your root password, and activate 3rd party drivers. 

I'm stuck on a windows box right now, so I'm sorry if what I said is not entirely accurate.

---

### Post by marshag63 on 2011-02-25
Ahh, it is the wired ethernet connection.  Check what eth0 interface shows:  Type "ifconfig" in a terminal and see what it reports back.

MDG

---

### Post by Kr1 on 2011-02-25
> **marshag63 said:**
> Ahh, it is the wired ethernet connection.  Check what eth0 interface shows:  Type "ifconfig" in a terminal and see what it reports back.

MDG
Here is what it reports back:

eth0      Link encap:Ethernet  HWaddr 00:1b:24:b5:70:fc  
          inet6 addr: fe80::21b:24ff:feb5:70fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207057 (207.0 KB)  TX bytes:69970 (69.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:ce:ae:05  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fece:ae05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36339106 (36.3 MB)  TX bytes:7153024 (7.1 MB)

> **rhoparkour said:**
> In order to clarify, you have a working wireless connection?

If so, go to System > Administration > Drivers (or something like this)*.

Input your root password, and activate 3rd party drivers. 

I'm stuck on a windows box right now, so I'm sorry if what I said is not entirely accurate.
I have my nnvidia driver installed now but I want also my ethernet too work :)

---

### Post by marshag63 on 2011-02-25
Thanks for posting back.

I don't see your eth0 inet addr, Bcast or Mask,  but by the rest of the entry everything looks fine.  So, unless you have both ehthernet cable plugged in and wifi active at the same time - I'd say restart the network manager by double clicking the networking icon, after you make sure wifi is turned off.

Let us know if restarting network manager helped or if you get an error message.

MDG

---

### Post by Newuser9 on 2011-03-10
I'm having a similar problem. My computer is a desktop without wireless but it comes up with a wireless symbol with an exclamation mark on it. It can't get my mouse drivers so my mouse doesn't work when I boot. This is really troubling since I installed using the same disk onto my usb drive which I'm posting from right not. It works fine. I'm also rather new to Ubuntu. so given that my mouse is frozen any help will need to give keyboard short cuts please :)

---

### Post by marshag63 on 2011-03-11
Do you have a different mouse you can try?

What are the specs of this computer?

MDG

---

