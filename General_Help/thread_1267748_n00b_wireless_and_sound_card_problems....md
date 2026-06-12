---
title: "n00b wireless and sound card problems..."
date: 2009-09-16
forum: General Help
---

### Post by frlan.jb on 2009-09-16
I'm sorry to have to post here...I'm brand new to using any kind of linux os, and i've been searching this forum for 3 days before making a post...but i'm just lost! I am dual booting Windows Vista 64 bit and Ubuntu 8.04 x86_64 on my HP dv6 laptop. I'm trying to configure my wireless card and my sound card...both of which are not working. 

A note on the sound card, when I play audio, I can hear what's playing but it is only BARELY audible through headphones! (i've checked to make sure my volume levels are up. other than that, i'm stumped.)

here's what I got when i ran the lspci command:

joel@joel-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. Unknown device 002b (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)




thanks for any help you can give me!

---

### Post by gettinoriginal on 2009-09-16
Hi, welcome to ubuntu :P   For sound, go [here]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")
And for wireless go [here]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")  

P.S. When searching I use googlubuntu   :P

---

### Post by frlan.jb on 2009-09-16
thanks, however i followed the instructions for the sound solutions, and still no go. i downloaded the synaptics packages, made sure my login was a member of all the pulse groups, rebooted, and then i got lost because I wasn't sure about which hardware device to select in the playback box for the PulseAudio Device Chooser. 

here's a sreenshot of my preferences window:

[IMG]http://i32.tinypic.com/2wnwgg3.jpg[/IMG]

and again, here is a list of my hardware:

```
joel@joel-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. Unknown device 002b (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

```
thanks for the help! even though it's frustrating, i'm enjoying the process of learning!

---

### Post by gettinoriginal on 2009-09-16
Mine is set as below, except you would want to select ATI HDMI, to try, and if that does not work, then choose ATI SB
[ATTACH]128819[/ATTACH]

---

### Post by frlan.jb on 2009-09-16
i set my card to hdmi, still no sound. thanks for the tip on googlubuntu, i searched and was able to find some more alsa information in the troubleshooting section...i can't tell whether my sound card is supported by alsa or not, any help?

here's a link to my alsa information:

[http://www.alsa-project.org/db/?f=e5a2d4db82f3daa1ce87ab9c43b57a7d990a20e0](http://www.alsa-project.org/db/?f=e5a2d4db82f3daa1ce87ab9c43b57a7d990a20e0)

thanks for any help

---

### Post by gettinoriginal on 2009-09-17
Alsa does recognize your HDI card, now I would right click your sound icon, and make sure that nothing is muted.

---

