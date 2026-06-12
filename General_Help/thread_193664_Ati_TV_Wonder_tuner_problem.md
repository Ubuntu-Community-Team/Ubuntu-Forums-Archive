---
title: "Ati TV Wonder tuner problem"
date: 2006-06-10
forum: General Help
---

### Post by rlange on 2006-06-10
I am having a problem  with my ati tv wonder since upgrading to Dapper. I have an nvidia 6800 gt video card. When the card was working in Breezy I created a launcher using the command
"xawtv -c /dev/video0" which I was using to launch xawtv this no longer works in Dapper. Device manager sees  Conexant CX23880/1/2/3 PCI Video and Audio. I tried reinstalling xawtv to no avail.

Anyone have any ideas?

Thanks

---

### Post by emperor on 2006-06-10
open a terminal and type "dmesg |less" 
then go though the messages to see if your card was detected and what the /dev assignments were.

---

### Post by rlange on 2006-06-10
output from dmesg |less

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May
23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f5080
[4294667.296000] On node 0 totalpages: 262128
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32752 pages, LIFO batch:7
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f8f70
[4294667.296000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[4294667.296000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff30c0
[4294667.296000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fff7b80
[4294667.296000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff7ac0
[4294667.296000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:15 APIC version 16
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: BIOS IRQ0 pin2 override ignored.
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
:



```

---

### Post by emperor on 2006-06-10
Thats only the first page, use the space bar and arrow keys to find the section that releates to the tv card

---

### Post by rlange on 2006-06-10
I think this is the section we are looking for:
```
[4294685.508000] input: Logitech Logitech USB Keyboard as /class/input/input3
[4294685.508000] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-2
[4294685.518000] cx2388x v4l2 driver version 0.0.5 loaded
[4294685.518000] **** SET: Misaligned resource pointer: f7dcfd02 Type 07 Len 0
[4294685.518000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[4294685.518000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 217
[4294685.518000] CORE cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[4294685.518000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[4294685.531000] input: Logitech Logitech USB Keyboard as /class/input/input4
[4294685.531000] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-2
[4294685.531000] usbcore: registered new driver usbhid
[4294685.531000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294685.720000] cx88[0]/0: found at 0000:02:08.0, rev: 5, irq: 217, latency: 32, mmio: 0xfb000000
[4294686.119000] parport: PnPBIOS parport detected.
[4294686.119000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294686.188000] tuner 2-0060: All bytes are equal. It is not a TEA5767
[4294686.188000] tuner 2-0060: chip found @ 0xc0 (cx88[0])
[4294686.188000] tuner 2-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[4294686.231000] tda9887 2-0043: chip found @ 0x86 (cx88[0])
[4294686.235000] cx88[0]/0: registered device video0 [v4l2]
[4294686.235000] cx88[0]/0: registered device vbi0
[4294686.240000] **** SET: Misaligned resource pointer: f7dcf502 Type 07 Len 0
[4294686.241000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[4294686.241000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 225
[4294686.253000] ts: Compaq touchscreen protocol output
[4294686.270000] r8169 Gigabit Ethernet driver 2.2LK loaded
[4294686.270000] **** SET: Misaligned resource pointer: f7ec1f02 Type 07 Len 0

```

---

### Post by emperor on 2006-06-10
What is the output of:

xawtv -hwscan

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]What is the output of:

xawtv -hwscan[/QUOTE]

rick@superrig:~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
looking for available devices
port 274-274
    type : Xvideo, image scaler
    name : NV17 Video Overlay

port 275-275
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 276-307
    type : Xvideo, image scaler
    name : NV05 Video Blitter

port 308-308                            [ -xvport 308 ]
    type : Xvideo, video overlay
    name : NVIDIA Video Interface Port

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : ATI TV Wonder Pro
    flags: overlay capture tuner

---

### Post by emperor on 2006-06-10
try xawtv without the additional options in a terminal:

xawtv

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]try xawtv without the additional options in a terminal:

xawtv[/QUOTE]


I just get a black screen no sound either. Something else i noticed since upgrade is that VLC no longer has video but has sound.

output

```
rick@superrig:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
config: invalid value for norm: NTSC-M
valid choices for "norm": "ntsc", "pal"

```

---

### Post by emperor on 2006-06-10
try:

xawtv -device /dev/video0

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]try:

xawtv -device /dev/video0[/QUOTE]

output thanks btw

rick@superrig:~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65
rick@superrig:~$

---

### Post by emperor on 2006-06-10
The latest nvidia drivers may no longer support DGA. So try starting xawtv with the nodga flag.

[http://marc.theaimsgroup.com/?l=linux-video&m=113658102604512&w=2](http://marc.theaimsgroup.com/?l=linux-video&m=113658102604512&w=2)

xawtv -device /dev/video0 -nodga

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]The latest nvidia drivers may no longer support DGA. So try starting xawtv with the nodga flag.

[http://marc.theaimsgroup.com/?l=linux-video&m=113658102604512&w=2](http://marc.theaimsgroup.com/?l=linux-video&m=113658102604512&w=2)

xawtv -device /dev/video0 -nodga[/QUOTE]

getting closer white screen with audio. output

rick@superrig:~$ xawtv -device /dev/video0 -nodga
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_G_FBUF(capability=0x0 [];flags=0x0 [];base=(nil);fmt.width=0;fmt.height=0;fmt.pixelformat=0x00000000 [....];fmt.field=ANY;fmt.bytesperline=0;fmt.sizeimage=0;fmt.colorspace=unknown;fmt.priv=0): Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

---

### Post by emperor on 2006-06-10
Try fiddling with the setting in xawtv and perhaps run the scantv utility.
Are you using cable tv, satellite or is the signal from an antenna?
PAL, NTSC or ? In one post below it said xawtv was set to NTSC-M
[http://linux.bytesex.org/xawtv/](http://linux.bytesex.org/xawtv/)

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]Try fiddling with the setting in xawtv and perhaps run the scantv utility.
Are you using cable tv, satellite or is the signal from an antenna?
PAL, NTSC or ? In one post below it said xawtv was set to NTSC-M
[http://linux.bytesex.org/xawtv/](http://linux.bytesex.org/xawtv/)[/QUOTE]

 i am using cable tv ntsc,

is there another program to use for my tuner card or would i be better off with a different card? Or maybe install an older nvidia driver??

---

### Post by emperor on 2006-06-10
try "tvtime" - in "universe"
It defaults to /dev/video0

---

### Post by rlange on 2006-06-10
[QUOTE=emperor]try "tvtime" - in "universe"
It defaults to /dev/video0[/QUOTE]

Well thanks for all your help. I tried tvtime and kdetv and no luck with the video.

---

### Post by jinx099 on 2006-06-10
I'm also having ATI TV wonder problems with xawtv.  When I start it it goes to a black screen which i then have to ctrl-alt-backspace out.  I tried the -nodga option and it didnt change anything.  Heres my -hwscan output:

```
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : ATI TV Wonder Pro
    flags: overlay capture tuner


```

I have an x800 GTO working with the fglrx driver.

---

### Post by Jason_25 on 2006-06-10
[QUOTE=rlange]Well thanks for all your help. I tried tvtime and kdetv and no luck with the video.[/QUOTE]

tvtime should be working.  Make sure you have the nvidia drivers installed properly.

---

### Post by jinx099 on 2006-06-10
I found some interesting data while my computer was black screened.  I ssh'd into it and found that cpu usage was a 0%.  I also killes the xawtv process and my screen did NOT come back.

I tried tvtime and I'm getting this error:

```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/jinx/.tvtime/tvtime.xml"
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

---

### Post by emperor on 2006-06-10
The message seems to indicate that you must have an AIW (All in Wonder) card, video card & tv tuner combo. The ATI AIW cards do not have v4l compatible hardware which is supports by the GATOS project. I used to use AIW cards but no more! But looking at a previous post, this appears to NOT be the case!

---

### Post by Jason_25 on 2006-06-10
That error means your nvidia driver is not installed properly.  You either need nv or nvidia installed for tvtime.  Vesa won't work.

---

### Post by rlange on 2006-06-12
With the latest updates from Automatix I can now use TVtime. The colors are less than perfect but it is usable. I will try to tweek it in the near future.

---

### Post by Jason_25 on 2006-06-12
[QUOTE=rlange]With the latest updates from Automatix I can now use TVtime. The colors are less than perfect but it is usable. I will try to tweek it in the near future.[/QUOTE]
For me, the only thing wrong is contrast initially.  Try setting contrast in tvtime to 25.

---

### Post by jinx099 on 2006-06-17
bump, mine still isnt working :(

---

### Post by emperor on 2006-06-18
[quote=jinx099]bump, mine still isnt working :([/quote]

what does "dmesg" indicate about your card.
also "lspci" output
Version number of card, chipset and etc would be helpful.

Is this the ATI Wonder Pro a std PCI card, or one of the newer PCIx buses?

---

### Post by jinx099 on 2006-06-18
[QUOTE=emperor]what does "dmesg" indicate about your card.
also "lspci" output
Version number of card, chipset and etc would be helpful.

Is this the ATI Wonder Pro a std PCI card, or one of the newer PCIx buses?[/QUOTE]

```
jinx@triplea-u:~$ dmesg |grep ATI

[17179592.400000] CORE cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[17179592.496000] drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[17179592.692000] tuner 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179608.240000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.


jinx@triplea-u:~$ dmesg |grep ati

[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[17179569.296000] Calibrating delay using timer specific routine.. 4504.15 BogoMIPS (lpj=9008302)
[17179572.052000] ALI15X3: not 100% native mode: will probe irqs later
[17179575.948000] Driver 'sd' needs updating - please use bus_type methods
[17179589.664000] scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices
[17179592.496000] usbcore: registered new driver ati_remote
[17179592.496000] drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[17179592.504000] drivers/usb/input/ati_remote.c: Weird data, len=1 ff 00 00 00 00 00 ...
[17179617.796000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179617.924000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179627.836000] /dev/vmnet: hub 1 does not exist, allocating memory.
```

```
jinx@triplea-u:~$ lspci
0000:00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
0000:00:01.0 PCI bridge: ALi Corporation: Unknown device 524b
0000:00:02.0 PCI bridge: ALi Corporation: Unknown device 524c
0000:00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
0000:00:05.0 PCI bridge: ALi Corporation AGP8X Controller
0000:00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
0000:00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
0000:00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:11.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 40)
0000:00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
0000:00:12.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10)
0000:00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5569
0000:04:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 03)
0000:04:06.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:04:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:04:07.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:04:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

```

I don't know the version number or chipset of the card, i could look if it's really important.  It's the standard PCI version of the ATI tv wonder pro with the remote control.  The RC is also not working, but one thing at a time.

---

### Post by emperor on 2006-06-18
Most likely the tuner assignment is incorrect. Sometimes things get broken along the way and then fixed in another kernel release. There are some reports on the v4l list of tuner problems in FC5 that were working in FC4.

I would submit your problem to the v4l mailing list (link below). There is a link on the page to sign-up and search the archives. These guys know everything about this subject.

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

---

