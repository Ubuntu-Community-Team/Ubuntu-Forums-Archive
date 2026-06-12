---
title: "No HDMI signal after gdm service stop"
date: 2012-06-22
forum: General Help
---

### Post by SterlingM on 2012-06-22
I am trying to run Xorg -configure. But I have to do gdm service stop first.

Whenever I run "sudo gdm service stop", my monitor turns black and it gets no signal from the computer. I try to ctrl+alt+f1 over to a command line, but my monitor won't do anything. I eventually have to restart my computer. The monitor is connected through HDMI. lspci is - 
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [ATI Radeon HD 6800 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
Can anyone tell me why this might be happening? Any help is appreciated.

---

### Post by papibe on 2012-06-22
Hi SterlingM.

First off all, you don't need to stop gdm (or lightdm on 12.04) to run 'X -configure'. That just creates a new xorg.conf usually in the place you run it. Then you move it to its location and restart.

In the case you really want to stop gdm to do this. Go first to the text mode by pressing Ctrl+Alt+F1, and run the commands from there.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by SterlingM on 2012-06-23
I tried just going into a gnome terminal and typing "Xorg -configure" and "X -configure" and they give the same error. It says 
```

Fatal server error:
Server is already active for display 0
     If this server is no longer running, remove /tmp/.X0-lock and start again.

```

So I log out and hit ctrl+alt+f1, login, and try it from there. I get the same message. I booted into recovery mode and tried there. That told me it "could not create a lock on the /tmp/.tX0-lock file."

What does this all mean? How can I get an xorg.conf file? Will a reinstall help anything?

---

