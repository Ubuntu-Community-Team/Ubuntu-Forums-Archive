---
title: "Essential Drivers, I can't install them! (First timer)"
date: 2012-07-31
forum: General Help
---

### Post by Kamon489 on 2012-07-31
Hey all I just got Ubuntu for my new laptop, However I cannot find the drivers to work the laptop with Ubuntu. 

I have tried running programs such as Wine, etc. but no drivers will ever install regardless if I have my Ethernet cable in or not. It runs into constant error after error

The drivers I need can be found here: 
Model = (W150ERM/W150ERQ/W170ER)
[http://www.clevo.com.tw/en/e-services/Download.asp](http://www.clevo.com.tw/en/e-services/Download.asp)

My Notebook is here:
[http://www.ibuypower.com/Store/Battalion_101_W150ERQ_Gaming_Laptop](http://www.ibuypower.com/Store/Battalion_101_W150ERQ_Gaming_Laptop) (With some other modifications done)

I will be at work until about 7pm today but I will try to update when I can from my Phone, but thank you for all the help in advance! these forums look very friendly and extremely helpful. I Posted the essential information I suppose, but if there is anything I've left out please let me know

---

### Post by mastablasta on 2012-07-31
drivers for what exactly?
 
In linux drivers are part of kernel. WIndows drivers won't work in linux.
 
If you have nvidia/intel hybrid graphcis combo (called nvidia Optimus) it is not supported by Nvidia in linux. some had success using 3rd party software (community open source projects) such as bumblebee and ironhide. you should look for those.
 
as for any other drivers. what exactly is not working that you think it needs additional drivers?
command
```
lshw
```
will list hardare
```
 
lspci 

```
 
will list pci devices.

---

### Post by Mark Phelps on 2012-07-31
Just so you know ... Wine is NOT a Windows emulator; thus, it can't be used to install drivers.  As mastablasta already mentioned, you need Linux drivers, not Windows drivers -- so those driver downloads won't do you any good.

If something specific is NOT working, it's best to tell us that, rather than trying to install drivers.

---

### Post by techvish81 on 2012-07-31
actually most of the drivers come preinstalled in ubuntu kernel and you have to do nothing, 
only some proprietory drivers for particular graphic cards or wireless cards are sometime needed to install,  if they are really needed, normally the system notifies you about them.  

if you try to install windows driver in ubuntu they are not going to work..

to be more specific, what errors are there?

---

### Post by defcronyke on 2012-07-31
I just finished configuring a very similar model with Linux Mint 13 (the Clevo W150ERM), and everything works out of the box except the proprietary NVidia driver, so I will assume you're talking about your video card drivers not working properly. If your model is like the one I set up, it uses NVidia Optimus, and it likely has no built-in way of switching between video devices (no BIOS options or anything). NVidia doesn't support Optimus on Linux, but luckily the bumblebee project has a working solution.

If you want to get the NVidia proprietary driver working and there really is no option on your machine to switch between video devices, you should take a look at the recipe I wrote for getting the Optimus GeForce GT650M working with bumblebee. The full instructions are here: [http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

My recipe has only been tested on Linux Mint 13 Cinnamon, but I think it should work without any modifications on Ubuntu.

And sorry if I interpreted your question wrong, in that case please disregard my reply.

---

### Post by Kamon489 on 2012-07-31
> **Mark Phelps said:**
> Just so you know ... Wine is NOT a Windows emulator; thus, it can't be used to install drivers.  As mastablasta already mentioned, you need Linux drivers, not Windows drivers -- so those driver downloads won't do you any good.

If something specific is NOT working, it's best to tell us that, rather than trying to install drivers.

Haha, sorry.. Again a first time user 
and its SPECIFICALLY my network driver, I can't connect to any wireless networks at all. It doesn't even show up with network connections on my Wifi Options so I assumed it was my network drivers not working well. 

I also went into the system drivers and it says nothing is installed, I tried to put 2 and 2 together

> **techvish81 said:**
> actually most of the drivers come preinstalled in ubuntu kernel and you have to do nothing, 
only some proprietory drivers for particular graphic cards or wireless cards are sometime needed to install,  if they are really needed, normally the system notifies you about them.  

if you try to install windows driver in ubuntu they are not going to work..

to be more specific, what errors are there?

Well, I figured out what the errors were from after you guys said Wine isn't used to run all Windows Applications per-say


Mainly my problem is I can't connect to ANY wireless networks, it doesn't show anything is up in my area even. Which I figured would be a Network Driver mishap
I was tinkering with the "Add New Wireless Connections" thing and I tried to put in my SSID and all but it just WONT WORK

---

### Post by idoitprone on 2012-08-01
> **Kamon489 said:**
> Haha, sorry.. Again a first time user 
and its SPECIFICALLY my network driver, I can't connect to any wireless networks at all. It doesn't even show up with network connections on my Wifi Options so I assumed it was my network drivers not working well. 

I also went into the system drivers and it says nothing is installed, I tried to put 2 and 2 together



Well, I figured out what the errors were from after you guys said Wine isn't used to run all Windows Applications per-say


Mainly my problem is I can't connect to ANY wireless networks, it doesn't show anything is up in my area even. Which I figured would be a Network Driver mishap
I was tinkering with the "Add New Wireless Connections" thing and I tried to put in my SSID and all but it just WONT WORK

```
ctrl+alt+t
```

type in the prompt

```
lspci -nnk
```

use your mouse and copy paste the output to this forums

---

### Post by Kamon489 on 2012-08-01
> **idoitprone said:**
> ```
ctrl+alt+t
```type in the prompt

```
lspci -nnk
```use your mouse and copy paste the output to this forums

```
phillip@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fd1] (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel modules: nouveau, nvidiafb
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:1550]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by Kamon489 on 2012-08-01
bump, still need help

---

### Post by idoitprone on 2012-08-02
> **Kamon489 said:**
> bump, still need help

blame realtek for pushing hardware without proper drivers

here is the instructions to install it

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by robtygart on 2012-08-02
The very first place I go after installing Linux is Settings>additional drivers.

---

