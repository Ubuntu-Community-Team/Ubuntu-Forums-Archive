---
title: "can't anyone help with no internet after fresh install"
date: 2010-11-07
forum: General Help
---

### Post by mejbr2003 on 2010-11-07
installed ubuntu 10 desktop edition from download. next to vista on an acer aspire desktop. with a wired ethernet connection. straight from modem, no router.
internet works fine in vista.
I'm pretty much a noob and have exhausted my short list of things to try.
any ideas?

---

### Post by sikander3786 on 2010-11-07
Do you see the netwroking applet in system tray? Right click and see if Enable Networking is ticked. If it is, go to Edit Connections and see if a connection is defined there. It should be name eth0. If it isn't Add a new connection with all your parameters.

If eth0 is already listed, select and Edit it and on the IPv6 tab, set IPv6 to ignore.

---

### Post by mejbr2003 on 2010-11-07
it says "autoetho" and the ipv6 is already set to ignore

---

### Post by sikander3786 on 2010-11-08
Please post the output of

```
sudo lshw -C network 
```

And

```
ifconfig 
```

You can see this for a workaround.

[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by mejbr2003 on 2010-11-08
thanks for the response
here's the output of lshw -c network and ifconfig


New Note 7

roth@thetempleofsyrinx:~$ sudo lshw -c network
[sudo] password for roth: 
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:b5:4d:37
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:44 memory:fe02b000-fe02bfff ioport:d800(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
roth@thetempleofsyrinx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:b5:4d:37  
          inet6 addr: fe80::21d:72ff:feb5:4d37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6087 (6.0 KB)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9360 (9.3 KB)  TX bytes:9360 (9.3 KB)

roth@thetempleofsyrinx:~$

---

### Post by Hippytaff on 2010-11-08
this might be worth a read [http://www.nvidia.com/object/linux_nforce_1.11.html](http://www.nvidia.com/object/linux_nforce_1.11.html)
:-)

---

### Post by wojox on 2010-11-08
> **mejbr2003 said:**
> it says "autoetho" and the ipv6 is already set to ignore

Edit Auto eth0 and make sure "Connect Automatically" is checked.

---

### Post by mejbr2003 on 2010-11-08
it is checked

---

### Post by mejbr2003 on 2010-11-08
i don't see how the nvidia thing can help
but I really don't understand much of this at all
can you explain

---

### Post by mejbr2003 on 2010-11-08
should I just try reinstalling with an alternate download?

---

### Post by Hippytaff on 2010-11-08
I think it's possibly a driver issue, but I'm not sure of the differnce between the one you have (forcedeth) and forcedeth.c from the link I posted above^^

---

### Post by Hippytaff on 2010-11-08
> **mejbr2003 said:**
> should I just try reinstalling with an alternate download?

What do you mean by alternate download. Different version? :-)

---

### Post by mejbr2003 on 2010-11-08
forget I said that, i don't know what I mean
I'm fairly lost

---

### Post by mejbr2003 on 2010-11-08
the forcedeth driver thing looks as if it need to be installed at concurrent with initial installation

---

### Post by Hippytaff on 2010-11-08
What does
```

lspci

```return? :-)
to identify the Nvidia chipset and see if this might be an option :-)
[http://manpages.ubuntu.com/manpages/maverick/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/maverick/man4/nfe.4freebsd.html)

---

### Post by mejbr2003 on 2010-11-08
thank you here's lspci

roth@thetempleofsyrinx:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)
04:00.0 Communication controller: Agere Systems Device 0630 (rev 01)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
roth@thetempleofsyrinx:~$

---

### Post by Hippytaff on 2010-11-08
this is your chipset 
> 
Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)

This might be worth a try
[http://manpages.ubuntu.com/manpages/maverick/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/maverick/man4/nfe.4freebsd.html)

---

### Post by mejbr2003 on 2010-11-08
can you tell me how I go about adding lines to the kernel configuraton thingy

---

### Post by wojox on 2010-11-08
> **mejbr2003 said:**
> can you tell me how I go about adding lines to the kernel configuraton thingy

Try

```
gksudo gedit /etc/default/grub
```

Look for *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" *

and add it after splash. Then run 

```
sudo update-grub
```

---

### Post by mejbr2003 on 2010-11-08
when I enter gksudo gedit /etc/default/grub, 
there is no text, nothing about quiet splash

---

### Post by mejbr2003 on 2010-11-10
still unsolved

---

### Post by sikander3786 on 2010-11-10
> **mejbr2003 said:**
> when I enter gksudo gedit /etc/default/grub, 
there is no text, nothing about quiet splash
Please post the output of

```
cat /etc/default/grub
```

Please post even if it shows only an error message.

It would be better to just copy/paste the command from here to your terminal.

---

### Post by satish_j on 2010-11-10
can you ping to localhost??
how do you connect to Internet??meaning command used or what??

---

### Post by mejbr2003 on 2010-11-10
Hi guys, thanks for the response
below is the output for cat /ect/default/grub

and I see the line where I am supposed to insert "device miibus device nfe"

but How do I insert it. and, do you really think this is the fix?
hope so.

How do I connect to the internet?
I've been using ubuntu for almost 3 yrs, never had a connection problem. I use at&t, dsl, ethernet directly from the modem.
in the past, 
just clicking firefox would connect me.


New Note 7

roth@thetempleofsyrinx:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)
04:00.0 Communication controller: Agere Systems Device 0630 (rev 01)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
roth@thetempleofsyrinx:~$ 

any help is much appreciated

---

### Post by mejbr2003 on 2010-11-10
oh yeah, nope cant ping

---

### Post by sikander3786 on 2010-11-10
> but How do I insert it. and, do you really think this is the fix?
hope so.

Edit it by

```
gksudo gedit /etc/default/grub
```

Copy/paste the command as done previously. Make sure you don't change anything else than you intend to otherwise your system might go unbootable.

As **wojox** mentioned you need to put your entry here.

> Look for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add it after splash. Then run

```
sudo update-grub
```

However I feel it would be better to put it in between the quotes in this line

```
GRUB_CMDLINE_LINUX=""
```

Follow Wojox's suggestion first.

I don't know if it is really the fix or not but no harm in trying it.

Edit: Dont' dont forget to run sudo update-grub after changing the file or the changes might not take effect. If you get any errors, it would be better to post them before rebooting your system.

---

### Post by satish_j on 2010-11-10
> **mejbr2003 said:**
> oh yeah, nope cant ping

I think prob is with your network interface and not grub..can you post the output of /etc/network/interfaces file?

---

