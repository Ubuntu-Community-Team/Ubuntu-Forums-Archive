---
title: "No internet connection after updates"
date: 2011-06-25
forum: General Help
---

### Post by Stevic on 2011-06-25
Pretty much as the title says really. We updated my wifes laptop last night but this morning on trying to connect to the internet we were unable to do so and "Server not found" error message displayed.

Anyone got any ideas.

---

### Post by ClientAlive on 2011-06-25
> **Stevic said:**
> Pretty much as the title says really. We updated my wifes laptop last night but this morning on trying to connect to the internet we were unable to do so and "Server not found" error message displayed.

Anyone got any ideas.


Can you post the error message? If you can't copy/ paste it you could take a picture and attach it to your post. We all do that around here from time to time.

Oh, and, when you say "update" what do you mean? Do you mean you upgraded to a later release of Ubuntu like Ubuntu 11.04? What distro and release are you running anyhow?

---

### Post by Stevic on 2011-06-25
Unfotunately i can not post error message window but as i say "Server not found" appears after clicking Firefox icon ans saying to make sure i have typed in correctly.

We upgrade to 11.04 last night. It was connecting fine before upgrade.

---

### Post by ClientAlive on 2011-06-25
> **Stevic said:**
> Unfotunately i can not post error message window but as i say "Server not found" appears after clicking Firefox icon ans saying to make sure i have typed in correctly.

We upgrade to 11.04 last night. It was connecting fine before upgrade.


I apologize, I really do, but it's past 4 am where I live and I have to get to bed. I'd like to ask you some questions though and I think I can help. If not me, this will be information that can help anyone who comes along.

Can you give some details about the computer?

If it's a laptop I'm assuming you use a wireless connection? Do you happen to know if it has the broadcom wireless card in it?

Can you post the results of:

```
lspci
```

This will tell us what wireless card is in the computer.

Please first try:

```
lspci | grep Network
```

If that doesn't give any results then the first one. The first one gives this huge long list of stuff and only one of those lines, near the bottom is what we need to know to begin with. The second "Code" should give only the relevant information.

Also please show us/ post the output of:

```
rfkill list
```

That helps us identify where the problem might be.

To open a terminal you can press ctrl+alt+t and then just type each of those into it and paste the results here - one by one. You can copy the output in the terminal by highlighting it and then pressing ctrl+shift+c and then paste here. Start with the second "Code" I gave you. If, for some reason, it doesn't give you anything run the first one. Then try the last one. We can start troubleshooting from there.

I gotta go for now but I'll try and check on you in about 8 or 9 hrs if nobody else comes along.

Thanks
-----------------------

Edit:

Another good one is:

```
sudo lshw
```

Just paste the top section less the last line of that section.

Here's what mine looks like:

```

 description: Notebook
    product: HP Pavilion ze2000 (PV336AV#ABA)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF6020YMD
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp

```

Also past the part from the heading "*-network:0" to the end. It starts about half way down the list.

Here's what mine looks like:

```

  *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 10
                serial: 00:16:36:0b:ce:81
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
           *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:20 memory:c0204000-c0205fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:05:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:c0200000-c0200fff ioport:a400(size=256) ioport:a800(size=256) memory:40000000-43ffffff(prefetchable) memory:44000000-47ffffff
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003400-c00034ff
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003800-c00038ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:68:f7:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.10 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Thanks

---

### Post by grahammechanical on 2011-06-25
A server not found error message from a web browser could be caused by one of two things, or both.

1) The computer is not connected to the modem/router and for that reason cannot connect to the ISP for it to connect to the web site that the browser has been directed to.

2) The modem/router is not connected to the ISP. It is not unknown for the servers at the ISP to be not working for some reason.

What other information, apart from this web browser message, do you get? Does the Network Manager icon have a red exclamation mark against it? Have any error messages appeared just after the desktop has loaded informing you that you are disconnected.

When you click the network manager icon do you see any information that would indicate that you are not connected? Are you making a connection by ethernet or by wireless? Is there a tick mark against the lines Enable Networking and Enable Wireless? If not put the tick mark there by clicking on those lines.

I hope that some of this helps.

Regards.

---

### Post by Duncan Williams on 2011-06-25
getting to the absolute basics.
Is your internet connection setup in network manager?

I have to actually establish a connection by answering questions in network connections before it will work.

---

### Post by Stevic on 2011-06-25
All connections are ticked although enable wireless needs reticking on boot up. No exclamation marks.

---

