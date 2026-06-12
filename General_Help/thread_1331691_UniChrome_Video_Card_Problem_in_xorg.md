---
title: "UniChrome Video Card Problem in xorg"
date: 2009-11-19
forum: General Help
---

### Post by ommie ramirez-andujar on 2009-11-19
Hi, i am having trouble reaching the 1024x728 resolution, here's my
xorg.conf and my hardware lspci.

--START--
# xorg.conf (X.Org X Window System server configuration file)
# Edit this file with caution, and see the xorg.conf manual page.
# Type "man xorg.conf" at the shell prompt.
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
       Identifier  "VIA Technologies, Inc. KM400/KN400/P4M800 [S3
UniChrome] (rev 01)"
       Driver      "openchrome"
EndSection

Section "Monitor"
#  DisplaySize  312 234
 HorizSync    30-71
 Identifier   "Monitor[0]"
 ModelName    "SAMSUNG SYNCMASTER"
#  Option       "DPMS"
 VendorName   "SAM"
 VertRefresh  43-160
#  UseModes     "Modes[0]"
EndSection

#Section "Modes"
#  Identifier   "Modes[0]"
#  Modeline     "1280x1024" 93.04 1280 1352 1488 1696 1024 1025 1028 1055
#  Modeline     "1024x768" 93.16 1024 1088 1200 1376 768 769 772 806
#  Modeline     "1024x768" 83.00 1024 1080 1192 1360 768 769 772 803
#  Modeline     "1024x768" 73.89 1024 1080 1192 1360 768 769 772 799
#  Modeline     "1024x768" 64.11 1024 1080 1184 1344 768 769 772 795
#  Modeline     "800x600" 60.07 800 840 928 1056 600 601 604 632
#  Modeline     "800x600" 53.14 800 840 928 1056 600 601 604 629
#  Modeline     "800x600" 45.50 800 840 920 1040 600 601 604 625
#  Modeline     "800x600" 38.22 800 832 912 1024 600 601 604 622
#  Modeline     "768x576" 55.94 768 816 896 1024 576 577 580 607
#  Modeline     "768x576" 48.71 768 808 888 1008 576 577 580 604
#  Modeline     "768x576" 41.66 768 800 880 992 576 577 580 600
#  Modeline     "768x576" 34.96 768 792 872 976 576 577 580 597
#  Modeline     "1024x768" 94 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
#EndSection

Section "Screen"
       Identifier      "Screen0"
       Monitor         "Monitor0"
       Device          "openchrome"
       DefaultDepth 16
       SubSection "Display"
               Depth      15
               Modes      "1280x1024" "1024x768" "800x600" "768x576"
       EndSubSection
       SubSection "Display"
               Depth      16
               Modes      "1280x1024" "1024x768" "800x600" "768x576"
       EndSubSection
       SubSection "Display"
               Depth      24
               Modes      "1280x1024" "1024x768" "800x600" "768x576"
       EndSubSection
       SubSection "Display"
               Depth      8
               Modes      "1280x1024" "1024x768" "800x600" "768x576"
       EndSubSection
EndSection
--END--

--START--
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video
Broadcast Decoder (rev 01)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA
RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc.
VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1
Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge
[KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc.
VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem
Controller (rev 80)
01:00.0 VGA compatible controller: VIA Technologies, Inc.
KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
--END--

Any suggestions.

ommie

---

