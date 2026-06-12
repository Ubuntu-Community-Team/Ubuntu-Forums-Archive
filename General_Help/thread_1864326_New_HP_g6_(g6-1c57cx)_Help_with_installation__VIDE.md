---
title: "New HP g6 (g6-1c57cx) Help with installation / VIDEO PROBLEMS"
date: 2011-10-18
forum: General Help
---

### Post by crjackson on 2011-10-18
I just purchased a new HP g6 today. I want to install Ubuntu Oneiric - The problem is that I have to use the "nomodeset" option (otherwise I can't see the install screen, everything is black) to boot to a LiveCD desktop or install screen.

Once there, screen resolution is really bad, and desktop effects don't work at all so I'm in a 2D session.

If I go forward with the install, how do I get my graphics working properly?

lspci

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
ubuntu@ubuntu:~$ 

```

---

### Post by crjackson on 2011-10-18
I hope someone jumps in here tonight with some help. I need to get this done tomorrow if possible.

Thanks

---

### Post by crjackson on 2011-10-19
Okay, so I've searched hi/lo, and still don't know how to do this. Have you ever noticed that if you put something radical in the title that has little to do with the problem, people jump in and help you find a good solution without hesitation?

Describe your problem in the title and help may never come. I'm becoming temped to try this tactic. I guess I'm feeling the pressure from my wife wanting to use her new laptop.

---

### Post by crjackson on 2011-10-19
Would it help if I dare you to help me?

---

### Post by crjackson on 2011-10-20
Well it seems that no one here can help. I've found that 11.04 boots and seems to be working well (from LiveCD). Since no one wants to help me with installing Oneiric, I'll go with Natty.

---

### Post by crjackson on 2011-10-20
Marking this one solved. I got 11.04 to work on here but not 11.10.

Thanks for all the help...  Oh wait, I didn't get any...

---

