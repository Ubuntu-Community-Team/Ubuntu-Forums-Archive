---
title: "The sound of silence"
date: 2006-05-11
forum: General Help
---

### Post by jmpmjmpm on 2006-05-11
I have searhed high and low for a solution to my sound problem with Linux when running on my Packard Bell easynote a8202 laptop. I think the problem is with Linux not reconising the codec used in my Intel ICH6 on board sound device. I have looked through alsa bugtrack and although a bug has been submitted there seems to be no progress in fixing it.

My output of lspci is:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P
rocessor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM
L Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre
ss Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P
CI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                              y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                              y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR                                                              W (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97                                                               Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge                                                               (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family                                                              ) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus                                                               Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho                                                              st Controller
0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash                                                              Media Controller
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                                              /8139C+ (rev 10)

I bought this notebook in January and as it seemed to be a nice ultra portable, well it is, but I can't suffer in silence. This is the major problem that keeps my windows partition larger tahn my Kubuntu one!

If any of you guru's out there can help me fix this I would really appreciate it. (can I use oss instead of alsa?)

---

### Post by jmpmjmpm on 2006-05-12
sorry this is a double post, please help if you can at this thread  >>

[http://www.ubuntuforums.org/showthread.php?t=174303](http://www.ubuntuforums.org/showthread.php?t=174303)

---

