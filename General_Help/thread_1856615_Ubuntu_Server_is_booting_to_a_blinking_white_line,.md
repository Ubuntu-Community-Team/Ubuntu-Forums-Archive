---
title: "Ubuntu Server is booting to a blinking white line, not responsive."
date: 2011-10-08
forum: General Help
---

### Post by sirspazzolot on 2011-10-08
Both machines I've tried installing it on are old computers. On the laptop, it goes to the white line, but on an old desktop it sends my monitor to standby. I don't really care as much about getting it to boot on the desktop because it's noisy as hell but whatever.

I tried taking out the quiet and splash grub parameters but that doesn't show me anything. It just takes out the splash screen, and the blinking line appears a few lines lower than normal. I'll get the specs for y'all in a moment.

Installation process went fine. I installed via USB. Something I've noticed about this particular USB stick, though, is that every installation it does is broken if more than a week or so has passed since putting the OS image on the USB drive. Does that make sense somehow, or am I just crazy?

---

### Post by sirspazzolot on 2011-10-08
Intel Pentium M processor, 1.6GHz
Intel Mobile 915GM/GMS/910GML Express Graphics Controller
it says I have 487.1 MB of RAM (that implies my graphics card is integrated, right? I mean, I know it is, I just don't know how to tell.)

I can get a normal Ubuntu installation to boot wonderfully. Just not server.

EDIT: ```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
``` Here's the output of lspci. Just cuz.

---

### Post by sirspazzolot on 2011-10-08
I can boot into recovery mode and drop to a root shell, if that'll help me somehow. Help?

---

### Post by sirspazzolot on 2011-10-08
I should've thought of this at first. I just did that ctrl+alt+f2 thingy and it switched me to the other session thing. errythang is good. errythang is groovy.

---

