---
title: "LAN not working?"
date: 2010-06-01
forum: General Help
---

### Post by oaxacamatt1 on 2010-06-01
Hi All,
I cannot seem to get my wired network port working on my laptop.  Here is Lshw, lspci and ifconfig -a.  Any help would be really welcomed.
Cheers

dolly@dolly:~$ lshw
WARNING: you should run this program as super-user.
dolly                     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1883MiB
     *-cpu
          product: Genuine Intel(R) CPU             585  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 550MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:90000000-903fffff memory:80000000-8fffffff(prefetchable) ioport:4140(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:93400000-934fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:40c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:40a0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:96605400-966057ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:96600000-96603fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:95600000-965fffff ioport:90400000(size=16777216)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:94500000-955fffff ioport:91400000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:d2:2b:ad:e6
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:94500000-9450ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:1000(size=4096) memory:93500000-944fffff ioport:92400000(size=16777216)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:4080(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4060(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4040(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4020(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:96605000-966053ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:4138(size=8) ioport:4154(size=4) ioport:4130(size=8) ioport:4150(size=4) ioport:4110(size=16) ioport:4100(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:96605800-966058ff ioport:4000(size=32)
        *-ide:1
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:4128(size=8) ioport:414c(size=4) ioport:4120(size=8) ioport:4148(size=4) ioport:40f0(size=16) ioport:40e0(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage


dolly@dolly:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

dolly@dolly:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:2b:ad:e6  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d2ff:fe2b:ade6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6734309 (6.7 MB)  TX bytes:617055 (617.0 KB)

---

### Post by Bucky Ball on 2010-06-01
Have you tried System->Admin->Network and made sure you have the cable ticked, not wireless? It should happen when you plug a cable in but not always in my experience.

Other thing is: You know the ethernet cable is in working order?

---

### Post by rnerwein on 2010-06-01
hi
i think got the similar problem before my configurariton is:
lucid , suse, winXP all of them are connecte via WIFI to the net and all are connectet to a switch via wired to a switch.
lucid, suse and winXP are different boxes !
on lucid lynx my configuration in /etc/network/interfaces looks like this:
auto lo
iface lo inet loopback


# the eth0 interface
auto eth0
iface eth0 inet [COLOR=Blue]static[/COLOR]
address 193.149.32.76
netmask 255.255.255.0
broadcast 193.149.32.255

i ain't know if the static is the trick ( if you even use the switch to connect to the internet you have to configure your 
router too )
this configuration works* for me.
*mostely - sometimes the WIFI on lynx is disconnected ( randomly ) by self.
good luck
ciao

---

### Post by oaxacamatt1 on 2010-06-01
I just the cable and it seems OK. but nothing happened when I plugged in either cable.  I even turned off the wifi and this did not spur a LAN connection.  NO GO?

---

### Post by xifer on 2010-06-01
unless i miss it your wired port is not being recognised by linux.

what model laptop is this?

---

### Post by oaxacamatt1 on 2010-06-01
Laptop is Toshiba Satellite L305-5919 with a Realtek LAN built 10/100 on an Intel board.

CORRECTION: it is not a Realtek LAN that is the card reader the LAN is simply built on Intel board. Sorry.

FYI
[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2241927&rpn=PSLB8U&modelFilter=L305-S5919&selCategory=3&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2241927&rpn=PSLB8U&modelFilter=L305-S5919&selCategory=3&selFamily=1073768663)
==================

Actually dont see any flashing lights on the LAN at all???

---

### Post by oaxacamatt1 on 2010-06-01
Hmmm.  Interestingly my configuration file /etc/network/interfaces ONLY had this:
auto lo
iface lo inet loopback

So I added the part you had, ie:
# the eth0 interface
auto eth0
iface eth0 inet static
address 193.168.2.1
netmask 255.255.255.0

And got nothing as well.

---

### Post by xifer on 2010-06-01
had a quick look and i don't see any issues with your laptop - the wired ethernet should be fine.

[http://www.linlap.com/wiki/toshiba+satellite+l300d-l305d](http://www.linlap.com/wiki/toshiba+satellite+l300d-l305d)


you shouldn't need to edit /etc/network/interfaces - looks like your router is providing ip address nicely for your wireless adapter so it should be the same for the wired connection.

if you do define a static address you need to make sure your router doesn't assign that same address to another computer.

better would be like this so your router is asked for an address

```

auto eth0
iface eth0 inet dhcp


``` 

but you don't need anything in there.  Your hardware is not being recognised in the first place.  Does this port work ok when running windows on the laptop?

Can you connect using a USB cable to the router?

---

### Post by Bucky Ball on 2010-06-01
> **oaxacamatt1 said:**
> Hmmm.  Interestingly my configuration file /etc/network/interfaces ONLY had this:
auto lo
iface lo inet loopback

So I added the part you had, ie:
# the eth0 interface
auto eth0
iface eth0 inet static
address 193.168.2.1
netmask 255.255.255.0
**gateway 192.168.0.1**

And got nothing as well.

You are missing your gateway, which is the IP of your router. Change 192.168.0.1 to the appropriate one for your *router*.

oaxacamatt1, are you booting with the cable plugged in, not just plugging it in while the machine is running? Boot with it plugged in, still nothing, try this in a terminal and post the output:

```
sudo /etc/init.d/networking restart
```

---

### Post by oaxacamatt1 on 2010-06-01
Hey Bucky,

I have tried both ways ie wifi boot up and LAN cable only boot up.  But as per your suggestion:

dolly@dolly:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
                                                                         [ OK ]

---

### Post by Bucky Ball on 2010-06-01
Hmmm, interesting, but that doesn't help you much!

This is obviously the problem:

```
 eth0: ERROR while getting interface flags: No such device
```

... which gives the impression the device is dead or switched off. You could start investigating that. The cable was working fine before? You had the cable connection working in the past?

This might help for a static address:

[http://www.howtogeek.com/wiki/Fixing_%22Failed_to_bring_up_eth0%22_in_Ubuntu_Virtual_Machine](http://www.howtogeek.com/wiki/Fixing_%22Failed_to_bring_up_eth0%22_in_Ubuntu_Virtual_Machine)

... and you might find some clues here:

[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=eth0%3A+ERROR+while+getting+interface+flags%3A+No+such+device+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?fr=altavista&itag=ody&q=eth0%3A+ERROR+while+getting+interface+flags%3A+No+such+device+ubuntu&kgs=0&kls=0)

Let us know how it goes ...

---

### Post by Iowan on 2010-06-01
**sudo lshw -C network** will limit the output to networking devices - but it seems that the machine doesn't recognize the wired interface.

I tried looking up the machine on the web - but haven't found a source that mentions which wired chipset it uses.

---

### Post by oaxacamatt1 on 2010-06-02
> **Iowan said:**
> **sudo lshw -C network** will limit the output to networking devices - but it seems that the machine doesn't recognize the wired interface.

I tried looking up the machine on the web - but haven't found a source that mentions which wired chipset it uses.

Hi Iowan,
I'll try looking up or might even call in to get more info on the NIC.  In the meantime I tried the **sudo lshw -C network** and got these results:
===================================================
[105][mcc.dolly: /home/mcc]$ sudo lshw -C network
[sudo] password for mcc: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:d2:2b:ad:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:94500000-9450ffff
[106][mcc.dolly: /home/mcc]$ 
======================================================
Cheers,
M

---

### Post by Bucky Ball on 2010-06-02
Iowan, your tip, try madwifi perhaps?

---

### Post by oaxacamatt1 on 2010-06-02
Hey Guys or Girls (as they case May be),
Let me ax you question.  Is there something inherently different about 9.10 and 10.04 regarding the software or more precisely what software it uses compared to other systems. In other words, does all this work point to the idea that it is software related or more hardware related.  Can you answer that with the info we have?

I am starting to believe that this problem is due to a dead NIC on my motherboard.

---

### Post by Bucky Ball on 2010-06-02
Could be. ... and I did mention that possibility earlier. ;)

---

