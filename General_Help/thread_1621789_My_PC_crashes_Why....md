---
title: "My PC crashes Why...?"
date: 2010-11-14
forum: General Help
---

### Post by Michael12uk on 2010-11-14
My pc crashes time to time..
when run a antivirus program...Avast linux.
or just live on for to long..
this are the details of the last crash..

Well I am running ubuntu 10.04

hope someone can interpret that for me..

mich@mich-desktop:~$ dmesg|tail
[   78.012885] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.173.218.31 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=26907 DF PROTO=TCP SPT=40725 DPT=16615 WINDOW=5840 RES=0x00 SYN URGP=0 
[   79.125939] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.173.218.31 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=64472 DF PROTO=TCP SPT=40726 DPT=16615 WINDOW=5840 RES=0x00 SYN URGP=0 
[   82.699074] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.173.218.31 DST=192.168.1.2 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=21832 DPT=16615 LEN=110 
[   84.708191] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.173.218.31 DST=192.168.1.2 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=21832 DPT=16615 LEN=110 
[   88.718416] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.173.218.31 DST=192.168.1.2 LEN=130 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=21832 DPT=16615 LEN=110 
[   96.030509] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.13.43.187 DST=192.168.1.2 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=4290 DF PROTO=TCP SPT=57325 DPT=21832 WINDOW=8192 RES=0x00 SYN URGP=0 
[   96.031092] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.13.43.187 DST=192.168.1.2 LEN=47 TOS=0x00 PREC=0x00 TTL=118 ID=4291 PROTO=UDP SPT=3522 DPT=21832 LEN=27 
[   99.077922] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.13.43.187 DST=192.168.1.2 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=4301 DF PROTO=TCP SPT=57325 DPT=21832 WINDOW=8192 RES=0x00 SYN URGP=0 
[  105.039947] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=94.13.43.187 DST=192.168.1.2 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=4474 DF PROTO=TCP SPT=57325 DPT=21832 WINDOW=8192 RES=0x00 SYN URGP=0 
[  119.157220] Inbound IN=eth0 OUT= MAC=00:24:1d:8d:ab:ba:00:22:3f:37:b1:52:08:00 SRC=109.156.246.142 DST=192.168.1.2 LEN=136 TOS=0x00 PREC=0x00 TTL=112 ID=10596 PROTO=UDP SPT=13901 DPT=16615 LEN=116 

mich@mich-desktop:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	1028348	0	100
/dev/sda6                               partition	1560568	0	-1

ich@mich-desktop:~$ lspci -k
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
	Kernel driver in use: ohci_hcd
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
	Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
	Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
	Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
	Kernel driver in use: ohci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169

---

