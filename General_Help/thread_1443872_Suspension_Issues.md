---
title: "Suspension Issues"
date: 2010-03-31
forum: General Help
---

### Post by Blake. on 2010-03-31
When i close the lid on my laptop, it enters suspension. and when i come back, it does not respond in any way. No mouse, no keyboard, nothing. Its just frozen. It shows the image of log screen, but its frozen. Help?

---

### Post by Iowan on 2010-03-31
Which version? Some (I run Jaunty) let you configure what happens when you close the lid. Suspend seems to be a frequent problem - I try not to suspend.

---

### Post by Blake. on 2010-03-31
> **Iowan said:**
> Which version? Some (I run Jaunty) let you configure what happens when you close the lid. Suspend seems to be a frequent problem - I try not to suspend.

Ubuntu 9.10 Karmic Koala

---

### Post by Blake. on 2010-04-01
why is this moving so slow? last night i asked a question and got 2 pages of answers in like 45 minutes.

---

### Post by koolblue3 on 2010-04-01
Hi,

What hardware does your laptop use (Graphics card, cpu, etc)? Also, what graphics card driver are you using and does switching between virtual terminals help? To switch between virtual terminal hit ctrl+alt+F4 and then press ctrl+alt+F7.

---

### Post by Blake. on 2010-04-01
> **koolblue3 said:**
> Hi,

What hardware does your laptop use (Graphics card, cpu, etc)? Also, what graphics card driver are you using and does switching between virtual terminals help? To switch between virtual terminal hit ctrl+alt+F4 and then press ctrl+alt+F7.

Tried switching terminals, did not help. 

Hardware info:

IDK, i ripped all the stickers off my laptop.

---

### Post by koolblue3 on 2010-04-01
Hi,

Could you please run the ```
lspci
``` command in a terminal and post the output of that command.

---

### Post by Blake. on 2010-04-01
blakefebruary7@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by koolblue3 on 2010-04-01
Hi,

You could try changing the driver in /etc/X11/xorg.conf to "vesa" from its current setting and reboot, but remember the setting it is at now as you will need it later. After trying this, try to suspend and report back if it works.

---

### Post by Blake. on 2010-04-01
it won't let me save over it because i don't have permission modify system files.

Exact words of the message:

Could not save the file /etc/X11/xorg.conf. 

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by koolblue3 on 2010-04-01
Hi,

The reason you are getting that message is because you have to be root to edit it. To do this type in and run ```
sudo nano /etc/X11/xorg.conf
```. To save in Nano after editing is to hit ctrl+x and then when it says buffer modified hit the Y key and then when asked what file name to save as just hit enter.

---

### Post by Blake. on 2010-04-01
tried that, it actually made it worse. it put the original code back, still not working

---

### Post by koolblue3 on 2010-04-01
Hi,

This sounds like a bug. Are you running the open source "radeon" driver? It looks like the open source "radeon" driver is causing some suspend/resume problems. I have found two bug reports similar to yours. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544869) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438470](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438470).

---

### Post by Blake. on 2010-04-01
i have no idea. how can i check?

---

### Post by koolblue3 on 2010-04-01
> **Blake. said:**
> i have no idea. how can i check?

What was the original driver in the /etc/X11/xorg.conf file before I asked you to replace it with "vesa"?

---

### Post by Blake. on 2010-04-01
> **koolblue3 said:**
> What was the original driver in the /etc/X11/xorg.conf file before I asked you to replace it with "vesa"?

fglrx

---

### Post by koolblue3 on 2010-04-01
Hi,

You are using Ati's proprietary driver. This looks like a bug and similar issues have been reported, but have not been solved. I am not sure where to go from here. Maybe someone else has ideas?

---

### Post by Blake. on 2010-04-02
darn it. thanks for helping though.

---

