---
title: "poor transfer speed with samba and http"
date: 2011-04-22
forum: General Help
---

### Post by mr_arc on 2011-04-22
(this is a repost of the same thread in the networking/wireless forum, I think it's better suited here but couldn't see a way to move it)

I have a Proliant Microserver, I have Ubuntu Server 10.10 installed onto  to a USB stick (the server has an internal USB port). The storage  drives are Samsung SpinPoint F1s.

The server is plugged into a gbE switch, there is a link from that to a  200mbps powerline link, from there it goes to a 100mbps switch and then  to my machine I was testing from.

I realise that a powerline link can often slow things up, but I use the  same link for my Internet connection which will happily pull files down  at around 4.3mb/s.. so I know the link isn't the bottleneck.

If i copy anything via any of the samba shares then it transfers at  around 1.5mb/s. This speed does not change if I try plugging the client  into the same gbE switch as the server. Similar spees are shown if i  transfer it over http via apache2 as well.

Client machines are laptop running ubuntu and a win7 desktop. Speeds are the same copying to both of them.

I have applied tweaks to samba as described here;

[http://oreilly.com/catalog/samba/chapter/book/appb_02.html](http://oreilly.com/catalog/samba/chapter/book/appb_02.html)

lspci output -

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)

```iperf output (these were done on a wireless link, but still show way beyond what i see when using samba on a wired link)

Client reported;
```

[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  20.5 MBytes  17.1 Mbits/sec

```Server reported;
```

[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.2 sec  20.5 MBytes  16.8 Mbits/sec

```hdpram -t output;

```

/dev/sda1:
 Timing buffered disk reads:  340 MB in  3.00 seconds = 113.29 MB/sec

```I'm a newbie to Linux, and have run out of ideas - help!

---

### Post by mr_arc on 2011-04-24
looking at this again, I made an error.

The iperf speeds are in mbit/s and the samba ones I was looking at are in mbyte/s.. so they're very similar and it points the blame at the NIC - not samba?

just tried back on the gbE switch and am seeing transfers of 7.7MB/s to the laptop now.. which I guess close to showing up issue with my laptops nic

---

