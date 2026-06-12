---
title: "Help with virtualbox"
date: 2012-06-21
forum: General Help
---

### Post by mcwolves32 on 2012-06-21
100% cpu usage just opening to select which os too start any ideas? I have no clue new too linux.

---

### Post by mcwolves32 on 2012-06-21
bump
please help :(

---

### Post by cbanakis on 2012-06-21
Something does not seem right.

It has been my experience that virtual box uses very little resources compared to its counter parts.

Can you give more info?

Linux Distro?

Distro Version?

Processor/Ram?

Virtual Box Version?

---

### Post by Baulageng on 2012-06-21
don't know if this is the right forum to as this but here what i need help with:
I've installed Ubuntu 10.04 and Virtualbox 4.1.  I want to run  Virtualbox from the command line but acctually open the GUI, not be  headless.  I also want help for a script for Virtualbox to run  automatically each time i boot into command line that gives you a menu  of 2 or 3 different images to be run with virtualbox, each choice  representing a different image to be run. I have googled and found  scripts but they don't work,

---

### Post by coldraven on 2012-06-21
Try reading this 
[http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

---

### Post by mcwolves32 on 2012-06-21
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


lspci output

---

### Post by mcwolves32 on 2012-06-21
its a triple core amd with 4 gbs of ram..

---

### Post by QIII on 2012-06-21
How did you install VirtualBox?

---

### Post by mcwolves32 on 2012-06-22
via packages in synaptic. do i need too install additional files?

---

### Post by Habitual on 2012-06-22
Guest additions "may" help...[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by QIII on 2012-06-22
As might the Extension Pack, both of which can be found on Oracle's Virtualbox web page.

Incidentally, there is an Ubuntu repo available there.

[Www.virtualbox.org](Www.virtualbox.org)

---

### Post by john stiles on 2012-06-22
Are you sure you need to run 10.04? the new Ubuntu LTS 12.04 is now out and runs virtualbox 4.1 stably, and should run on the specs you specified. If there are bugs with 10.04, crosschecking with 12.04 wold be my strategy.

---

### Post by mcwolves32 on 2012-06-25
okay extensions didnt work and i cant install guest packages because i cant get into my vm at all as soon as i open virtual box to open windows 7 it jumps in processor and either freezes or goes so slow i have to close it

---

### Post by mcwolves32 on 2012-06-25
Should i try re installing it or what? Maybe another virtualization program?

---

### Post by mcwolves32 on 2012-06-25
what o.o

---

### Post by mcwolves32 on 2012-06-25
Tried several fixes ive seen on forums or bug trackers nothings working

---

### Post by cbanakis on 2012-07-02
As John Stiles suggested, might be time to upgrade to 12.04.

If your putting it off because of Unity, there are alternative configurations.
(Cairo-Dock, Gnome Classic, Cinnamon, etc)

If you have a hard drive laying around, you can test it out before making any irreversible changes.

---

