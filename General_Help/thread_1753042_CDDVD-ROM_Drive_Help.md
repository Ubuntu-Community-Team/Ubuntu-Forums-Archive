---
title: "CD/DVD-ROM Drive Help"
date: 2011-05-08
forum: General Help
---

### Post by I couldnt think of a name on 2011-05-08
I am trying to install GTA San Andreas onto my computer (using Ubuntu  11.04) and realised that I had to create a CD-ROM drive in Wine  Configuration.  I created the drive A: and made the path  "/media/cdrom/".  I clicked "Show Advanced" and made the type "CD-ROM".

After the installation finished I ran the file "Install.exe" (for the  game) and a window popped up providing the option to play the game.   After clicking it a window appeared reading: "No CD/DVD-ROM drive  found".

I believe the terminal read
"~$ fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d014
winecfg"

I am not entirely sure what any of this means and would definitely appreciate any help on how to get this game running (:.

By the way, I'm not sure if this will be of any importance, but here is  what popped up in the terminal after typing the command "sudo lspci  |more" to get information about the graphics card:

"00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller
 Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Int
egrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated
 Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (r
ev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (r
ev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 0
3)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) The
rmal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E P
CI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000"

--Thanks in advance

---

