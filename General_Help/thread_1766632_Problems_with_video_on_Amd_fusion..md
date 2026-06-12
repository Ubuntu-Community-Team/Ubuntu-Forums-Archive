---
title: "Problems with video on Amd fusion."
date: 2011-05-24
forum: General Help
---

### Post by GhostRider22 on 2011-05-24
I just recently built a new system, I am using the asus e35m1-l deluxe mobo. 

Has an e-350 onboard. My screen flickers, and lags, and is choppy on 720p, and 1080p video playback. I have not tested it on anything lower. However, flash videos also have problems, they lag, they flicker, there is black or white boxes covering small parts, or most of the video. This happens on multiple websites.


I installed the drivers for the video card, both through ubuntu, and from the ati website, however there is no effect. The computer generally seems laggy overall. It seems to run perfectly fine on vista. I've tried searching multiple places but to no avail. 



Thanks in advance for any help.

[IMG]http://i.imgur.com/0QQQC.png[/IMG]

Edit, this is an example, of my local weather radar.  I am assuming the problems with video performance and the flash playback is linked, but i guess its possible i have 2 problems.

---

### Post by el_koraco on 2011-05-24
For Flash, install the Flash-Aid plugin for Firefox. It will replace the current Flash plugin with the latest one from Adobe and tweak it (courtesy of the forum member lovinglinux). 

As for the screen flickering, that's might get tricky. The first thing to do is to install compizconfig-settings-manager. open the Software center and search for ccsm. Once you do that, if you're on 11.04, go to the OpenGL tab and uncheck the Sync to Vblank option. If you're on 10.10, go to the "General options" tab, under Display setting you should find the Sync to Vblank option. See if there are any improvements with the video. 

If that doesn't do the trick, run the following command in the terminal: 

```
aticonfig --sync-video=off
```

---

### Post by el_koraco on 2011-05-24
As for the general laggyness, open the ATI Catalyst control center (System, preferences in 10.10), Dash, type ATI in 11.04, and find the "Tear Free" option under Display options. Enable "Tear Free desktop".

---

### Post by sandyd on 2011-05-24
> **GhostRider22 said:**
> I just recently built a new system, I am using the asus e35m1-l deluxe mobo. 

Has an e-350 onboard. My screen flickers, and lags, and is choppy on 720p, and 1080p video playback. I have not tested it on anything lower. However, flash videos also have problems, they lag, they flicker, there is black or white boxes covering small parts, or most of the video. This happens on multiple websites.


I installed the drivers for the video card, both through ubuntu, and from the ati website, however there is no effect. The computer generally seems laggy overall. It seems to run perfectly fine on vista. I've tried searching multiple places but to no avail. 



Thanks in advance for any help.

[IMG]http://i.imgur.com/0QQQC.png[/IMG]

Edit, this is an example, of my local weather radar.  I am assuming the problems with video performance and the flash playback is linked, but i guess its possible i have 2 problems.
a) post output of ```
 lspci
```
b) The flash problem is normal. Flash sucks in linux. If your using 64-bit ubuntu, install 64bit flash.
c) The gallium mesa drivers work way better in terms of desktop performance. I switched from catalyst 11.5 (latest) to gallium svn, and the performance is totally unbelievable.

---

### Post by GhostRider22 on 2011-05-26
Here you go, i got flash working on chrome for now. 

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:15.2 PCI bridge: ATI Technologies Inc Device 43a2
00:15.3 PCI bridge: ATI Technologies Inc Device 43a3
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)


---

