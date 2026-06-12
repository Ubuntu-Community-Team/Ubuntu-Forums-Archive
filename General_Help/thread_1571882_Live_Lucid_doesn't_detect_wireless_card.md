---
title: "Live Lucid doesn't detect wireless card"
date: 2010-09-10
forum: General Help
---

### Post by t0p on 2010-09-10
I own an EeePC 701; right now I'm giving 10.04.1 a test run on it, using a live usb.

The EeePC has an Atheros wireless card, but live Lucid doesn't detect it.  Here's the output from a **ifconfig** command:

```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:0f:2a:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7200 (7.2 KB)  TX bytes:7200 (7.2 KB)

usb0      Link encap:Ethernet  HWaddr 02:80:37:19:03:00  
          inet addr:178.105.240.161  Bcast:178.105.240.163  Mask:255.255.255.252
          inet6 addr: fe80::80:37ff:fe19:300/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:852593 (852.5 KB)  TX bytes:103938 (103.9 KB)

ubuntu@ubuntu:~$ 

```

Will the card be detected by a properly-installed Lucid?  Is there some package I need to install so I can use wireless?  Or should I steer clear of installing Lucid on my EeePC?

---

### Post by plucky on 2010-09-10
What does ```
lspci
``` show you

---

### Post by t0p on 2010-09-10
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Atheros Communications L2 100 Mbit Ethernet Adapter (rev a0)
ubuntu@ubuntu:~$ 

```

I can't see my wireless interface there.

---

### Post by plucky on 2010-09-11
> Will the card be detected by a properly-installed Lucid? Is there some package I need to install so I can use wireless? Or should I steer clear of installing Lucid on my EeePC? 

The card is definitely not there in that list and I don't think a full install would help.

What Operating system do you have on there?
Does the wireless work with the current operating system? 
Could it be broken?

---

### Post by t0p on 2010-09-11
> **plucky said:**
> The card is definitely not there in that list and I don't think a full install would help.

What Operating system do you have on there?
Does the wireless work with the current operating system? 
Could it be broken?

The EeePC currently runs Eeebuntu 3 (basically 9.04 with some modifications) and wireless works just fine.  I have also used Intrepid briefly, and I think wireless worked.

So no, the wireless card is definitely *not* broken.  This is down to Lucid.  I know there are alternatives, but I would really like to use Lucid if possible.

---

