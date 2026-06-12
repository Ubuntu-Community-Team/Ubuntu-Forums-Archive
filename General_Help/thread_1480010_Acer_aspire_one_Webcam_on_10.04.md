---
title: "Acer aspire one Webcam on 10.04"
date: 2010-05-11
forum: General Help
---

### Post by tristan.cole on 2010-05-11
i have a acer aspire one ssd version. and have installed ubuntu 10.04, and my webcam has stopped working.

it always used to work in 9.10. but has now programs such as cheese says that i do not have a camara plugged in.

any help is appreciated

---

### Post by joao.taborda on 2010-05-24
i have the same problem...but i'm still on 9.10... just now i noticed the camera stoped working, i'm sure it worked already...maybe when using 9.04 long time ago...

if i run ```
lsusb
``` the camera is not listed at all...
with ```
dmesg | grep Crystal
``` nothing also

when i run the test in ```
gstreamer-properties
``` i only get a screen full of colors (like an old television)...

any clues?

---

### Post by no2498 on 2010-05-25
see if this helps
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope it helps

---

### Post by tristan.cole on 2010-05-30
I tried what you sayed but i got theses error messages:

when using v4l:
Video for Linux (v4l): Device "/dev/video0" does not exist

when using v4l2
Video for Linux 2 (v4l2): Device "/dev/video0" does not exist

and when i select the test option i get a screen with colour bars but no input from my webcam

---

### Post by joao.taborda on 2010-05-30
it looks like we are having the same problem...

what is your output for *lsusb*?

---

### Post by no2498 on 2010-05-31
have you 2 did this yet

sudo apt-get install ubuntu-restricted-extras


you wont see any thing as you type your pass word

---

### Post by tristan.cole on 2010-06-01
with nothing connected to my netbook i get this output:

$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and yes i have the latest version of ubuntu-restricted-extras

---

### Post by dino99 on 2010-06-01
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501743](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501743)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

[http://doc.ubuntu-fr.org/acer_aspire_one](http://doc.ubuntu-fr.org/acer_aspire_one)

---

### Post by no2498 on 2010-06-02
ok look in add remove
see if you have the gstreamer, good,bad,ugly installed you need all 3

---

### Post by joao.taborda on 2010-06-12
it looks like me and tristan.cole have the same problem, when doing lsusb on my aspire one i don't get the web cam nor the sdcard readers...

can anyone with aspire one post the "normal" lsusb output?

---

### Post by dinkydarko on 2010-06-13
i have the same bug.  have you tried that old kernel that was compiled for the aspire one?  i dont know how it differed from the current ubuntu kernel though.

---

### Post by joao.taborda on 2010-06-29
> **dinkydarko said:**
> i have the same bug.  have you tried that old kernel that was compiled for the aspire one?  i dont know how it differed from the current ubuntu kernel though.

i don't know which kernel are you talking about, but i already tried a live linux distr (not ubuntu) and got the same output with lsusb... i'm starting to think it's an hardware problem :-/...

would like to install back the linpus, the original OS in acer aspire one, to test if it would work, but can't find it online and lost the original cd when moving...

---

### Post by yokohama1234 on 2010-08-02
> **joao.taborda said:**
> i don't know which kernel are you talking about, but i already tried a live linux distr (not ubuntu) and got the same output with lsusb... i'm starting to think it's an hardware problem :-/...

lost the original cd when moving...

what does ***lspci*** or ***lspci -v***  output ?
which model of ***acer one*** do you own ?

do you know this site ? [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)


yokohama1234

---

### Post by joao.taborda on 2010-08-06
***lspci*** output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

***lspci -v*** output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 78480000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 60000000 (32-bit, prefetchable) [size=256M]
    Memory at 78500000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Memory at 78400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 78540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 77300000-783fffff
    Prefetchable memory behind bridge: 0000000070000000-0000000070ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 76300000-772fffff
    Prefetchable memory behind bridge: 0000000071000000-00000000720fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 75200000-762fffff
    Prefetchable memory behind bridge: 0000000072100000-00000000730fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 74100000-751fffff
    Prefetchable memory behind bridge: 0000000073100000-00000000740fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 78544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at 3000 [size=256]
    Memory at 71010000 (64-bit, prefetchable) [size=4K]
    Memory at 71000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 71020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 75200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 74100300 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 73100000 [disabled] [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: fast devsel, IRQ 19
    Memory at 74100200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 74100100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 74100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
```

i have [B]Acer Aspire One 110Ab

[/B]does it help something? :D
i'm still trying to figure out what's the problem

---

### Post by joao.taborda on 2010-08-28
still the same problem... and trying to solve it...

i don't get my camera or SD card readers working...

---

### Post by mxboy15u on 2010-09-01
I just wanted to bump this up, I just noticed that I am having this problem as well...wonder when the fix will be released? The bug report shows this as triaged whatever that means.

---

### Post by no2498 on 2010-09-01
see if any thing comes up if you type webcam in a terminal

---

### Post by mxboy15u on 2010-09-12
> **no2498 said:**
> see if any thing comes up if you type webcam in a terminal

It tries to install a program that uploads webcam images. 

Anyone else got any info on this problem?

---

### Post by Lukas666 on 2010-09-12
> **joao.taborda said:**
> i don't know which kernel are you talking about, but i already tried a live linux distr (not ubuntu) and got the same output with lsusb... i'm starting to think it's an hardware problem :-/...

would like to install back the linpus, the original OS in acer aspire one, to test if it would work, but can't find it online and lost the original cd when moving...

Could you please try this?

1. Shutdown
2. Unplug power supplier, remove battery
3. Wait for an hour.
4. Install battery and boot again.

---

### Post by dvalenca on 2011-04-16
I have a very similar (or the same) problem.
My webcam used to work on 9.10 and 10.04. Then I instaled the 10.10 and didn't work. So I did a fresh install from 10.04 and now it isn't work again.

It worked for a little, like, I turned on the cheese and work for seconds... now, I have the same messages that are written in the messages of this topic.

HELP! PLEASE!!!

(also the rigth SD doen't work and the mic on Skype - witch one I know how to fix, I think, with the padevcontrol)

---

### Post by dvalenca on 2011-04-16
Ok. I removed and re-installed Cheese and the WebCam worked again. But them, after a while, it stopped working.

Any clues?

There is a message in Cheese saying that it couldn't find a webcam...

---

### Post by no2498 on 2011-04-16
i just seen this

BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)

---

### Post by CaKiwi on 2011-05-13
The webcam on my Acer Aspire One ZG5 is also not working on 10.10. Cheese says "no device found". Anyone have a solution?

---

### Post by parapapapapa on 2011-07-06
same here on aspire one 150 zg5 
worked well on 10.04 for a while. But since 10.10 and 11.04 it doesnt work anymore.

---

### Post by joao.taborda on 2012-03-20
> **no2498 said:**
> 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..


I still have the same problem, my cam not working, and not being listed, i really think it's a hardware problem, but found it strange that so many people have it... to check it out only installing linpus again, will look for a live-usb with linpus...

the uvcvideo didn't work... did you mean dmesg instead of dmseg?

output was:
```
[  249.986686] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 3501.709298] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 3501.709316] ata2.00: BMDMA stat 0x4
[ 3501.709331] ata2.00: failed command: READ DMA
[ 3501.709359] ata2.00: cmd c8/00:00:98:e3:e9/00:00:00:00:00/e1 tag 0 dma 131072 in
[ 3501.709365]          res 51/84:00:98:e3:e9/00:00:00:00:00/e1 Emask 0x10 (ATA bus error)
[ 3501.709379] ata2.00: status: { DRDY ERR }
[ 3501.709390] ata2.00: error: { ICRC ABRT }
[ 3501.709449] ata2: soft resetting link
[ 3501.897552] ata2.00: configured for UDMA/100
[ 3501.897599] ata2: EH complete
[16887.491432] Linux video capture interface: v2.00
[16887.504664] usbcore: registered new interface driver uvcvideo
[16887.505449] USB Video Class driver (v0.1.0)
[16922.219671] usbcore: deregistering interface driver uvcvideo
[16923.951358] usbcore: registered new interface driver uvcvideo
[16923.951370] USB Video Class driver (v0.1.0)

```

---

