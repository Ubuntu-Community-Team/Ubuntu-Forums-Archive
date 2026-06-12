---
title: "upgrading kernel to 2.6.32 on ubuntu karmic loses wifi"
date: 2010-02-15
forum: General Help
---

### Post by libihero on 2010-02-15
haha title says it all.  when i upgrade my kernel my webcam begins to work (it doesnt work on this one), but my wifi stops working totally :(

---

### Post by libihero on 2010-02-17
bump...

---

### Post by libihero on 2010-03-22
bump...
this is a problem for me since lucid is coming up and my wifi wont work on there either....

---

### Post by pbrane on 2010-03-22
Did you have to install a driver to make your wireless work with the default kernel? If so you may need to re-install for the new kernel. Where did you get the kernel? Genereally if it worked before it should work now, if the card is supported by the kernel.

---

### Post by libihero on 2010-03-22
i got my kernel here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
and no i didnt have to install a driver to get my wireless working
its just with the 2.6.32 and higher kernels, it wont work on lucid either

---

### Post by pbrane on 2010-03-22
What kind of wireless card do you have? Maybe post *lspci* output. Have you looked on launchpad for any bug reports relating to your issue?

---

### Post by gadolinio on 2010-03-22
> **pbrane said:**
> What kind of wireless card do you have? Maybe post *lspci* output. Have you looked on launchpad for any bug reports relating to your issue?

Right, the solution may be to find the driver for your wireless card and kernel. I had this kind of issue in an Asus EeePC 1201N, and found the driver in launchpad.

---

### Post by libihero on 2010-03-22
here is my lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

how do i download the driver for it?

---

### Post by pbrane on 2010-03-22
Are you running the 2.6.32 kernel now? I don't see any wireless card in that output. Is this wireless device internal to your laptop or is it a PCMCIA or USB plugin? (I assume laptop, webcam and all...)

Maybe try *sudo lshw | grep -i wireless* and post that output.

---

### Post by libihero on 2010-03-22
i'm not using 2.6.32.... but i am connected to an ethernet cord for internet, will that make the wireless output turned off?

here is the output:
```
       description: Wireless interface
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=****** multicast=yes wireless=IEEE 802.11bg

```

i edited out the ip

---

### Post by libihero on 2010-03-22
solved :)
it disabled my wireless and i found out it was just a simple enabling by pressing function-F2 :)

---

