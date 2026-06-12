---
title: "Wifi Randomly DIsconnects.."
date: 2011-05-05
forum: General Help
---

### Post by maxwjackson on 2011-05-05
[COLOR=black][FONT=Verdana]I just upgraded from 10.10 to 11.04 (and hate it lol) but other than that the most annoying thing I've found is that my wifi will randomly disconnect from the network...like it will say its still connected but  pages wont load and all my torrents just stop, and then I have to manually disconnect from the network and then reconnect and it works for about a min and then happens again...kinda annoying.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I couldnt even get enough internet to post this from my laptop so I had to post this at school from a windows... :(  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Idk whats going on but it sucks because I cant really use the comp without the internet.. [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
:confused:

---

### Post by maxwjackson on 2011-05-05
bumpidy, need the internets lol

---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> bumpidy, need the internets lol

Yeah it sucks. I had it too.

Type this in Terminal.

```
lspci
```

Copy and paste all the output it gives you.

---

### Post by maxwjackson on 2011-05-05
.> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
max@max-HP-Pavilion-dv5-Notebook-PC:~$ 


---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> .

I would suggest blacklisting the driver in modprobe.d and using ndiswrapper instead. If that makes no sense don't worry lol.

---

### Post by maxwjackson on 2011-05-05
> **Shmantiv_Radio said:**
> I would suggest blacklisting the driver in modprobe.d and using ndiswrapper instead. If that makes no sense don't worry lol.
No idea what that means lol.

---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> No idea what that means lol.

Yeah this is where Ubuntu starts to suck. You basically add something to a text file which stops the operating system from loading the Linux WIFI driver. Then you use NdisWrapper to install the Windows WIFI driver.

---

### Post by maxwjackson on 2011-05-05
> **Shmantiv_Radio said:**
> Yeah this is where Ubuntu starts to suck. You basically add something to a text file which stops the operating system from loading the Linux WIFI driver. Then you use NdisWrapper to install the Windows WIFI driver.
Oh gotcha, I think I might downgrade to 10.10, I had no issues whatsoever, had it exactly how I wanted it, and then 11.04 messed everything up :(

---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> Oh gotcha, I think I might downgrade to 10.10, I had no issues whatsoever, had it exactly how I wanted it, and then 11.04 messed everything up :(

10.04 is uber stable. It's the LTS too (long term support).

---

### Post by maxwjackson on 2011-05-05
> **Shmantiv_Radio said:**
> 10.04 is uber stable. It's the LTS too (long term support).
It should be basically the same as 10.10?

I had my desktop perfect for me with the cube and 4 different backgrounds and compiz running perfect, I would assume I would be able to do the same on 10.04?

---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> It should be basically the same as 10.10?

I had my desktop perfect for me with the cube and 4 different backgrounds and compiz running perfect, I would assume I would be able to do the same on 10.04?

10.04 can do the cube yeah. Compiz should be fine if it worked in 10.10.

---

### Post by maxwjackson on 2011-05-05
> **Shmantiv_Radio said:**
> 10.04 can do the cube yeah. Compiz should be fine if it worked in 10.10.
Awesome thanks man!

:thumbsup:

---

### Post by Shmantiv_Radio on 2011-05-05
> **maxwjackson said:**
> Awesome thanks man!

:thumbsup:

No prob.

---

