---
title: "Computer locks up."
date: 2009-09-18
forum: General Help
---

### Post by LeeLgrqst on 2009-09-18
I have Ubuntu 9.04 64

My computer will lock up, and I won't be able to do anything.  I have to hit the reset button to get it working again.  Then sometimes it does it again in just a few minutes, other times it will go a day or two.  

I have no idea where to start to solve this problem, except for here.  This is also a computer I built myself, and I am by no means any kind of expert.

Here is a short list of what I have:
Motherboard: M3a78-EM
CPU:         AMD Athlon x2 - 5600
Video:       Radeon HD4850
Wireless:    wg311v3

Also, not sure if its related, but many times I get black boxes in whatever window I'm working in.  I included an example of what I'm talking about.  I followed the directions on the first link to a T (first link), when I installed the driver for the video card.

This is a fresh install, and I followed many of the directions given in the second link to complete my installation.

I also get a message during boot up that I can't read cause it goes away too fast.  Not sure if that is related either.  Just trying to provide you with as much relevant information as possible.

My main concern is to make the computer stop locking up.  If the display is an unrelated issue, I'll work on that some other time.  I just don't want to have to reset my computer all the time any more.  Thanks.

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

[http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/)

---

### Post by pveurshout on 2009-09-18
Hey, I'm also experiencing (seemingly random) lockups every now and then. Although I'm not sure whether we're having the same problem or whether I can help, could you check /var/log/messages after you experience a lockup and look for a message like:
```
[ 6234.705363] CE: hpet increasing min_delta_ns to 15000 nsec
[ 6234.705604] CE: hpet increasing min_delta_ns to 22500 nsec
[ 6962.600397] CE: hpet increasing min_delta_ns to 33750 nsec
[ 7356.076838] CE: hpet increasing min_delta_ns to 50624 nsec
[ 7900.620236] CE: hpet increasing min_delta_ns to 75936 nsec
```

In my case I'm suspecting this to be the cause, but I am neither sure whether it actually is (I'll try some stuff out in a few days and I'll let you know if I find something out, of course) nor can I say that your problem is related to it as well. But I guess it's worth a shot, wouldn't you agree? :)

---

### Post by hal10000 on 2009-09-18
@LeeLgrqst:

can you explain when and how often your systems locks up? Does it occur during boot time or in operation?
I suggest, next time your system locks up, notice date and time and then when you can boot it again, look into the file [COLOR="Red"]/var/log/messages[/COLOR] this file is sorted by date and time and you can find here system messages from the time when your system was locked up.
You may post them here, so we can find out what happened.

> Also, not sure if its related, but many times I get black boxes in whatever window I'm working in. I included an example of what I'm talking about. I followed the directions on the first link to a T (first link), when I installed the driver for the video card.
if you want the hardware accelerated ati drivers just type [COLOR="Red"][ALT + F2][/COLOR] and type in [COLOR="Red"]jockey-gtk[/COLOR], then press ENTER (if you use KDE, then instead of jockey-gtk do jockey-kde).

In the upcoming window choose your ati driver, press ok and when finished restart your gnome (or kde). That's all.

@pveurshout:
these are no error-messages, they are just messages from your hpet driver (High Precision Event Timer). In ma /var/log/messages file there are millions such entries and everything works fine.

---

### Post by LeeLgrqst on 2009-09-18
I was worried that it wouldn't lock up now for a few days, but it did.

The file was quite long, so I just copied from what I assume is when I started up to a little bit after it locked up.

Here it is:

```

Sep 18 10:28:47 lee-desktop kernel: [    3.779997] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (2 cpu cores) (version 2.20.00)
Sep 18 10:28:47 lee-desktop kernel: [    3.780061] powernow-k8:    0 : fid 0x15 (2900 MHz), vid 0x8
Sep 18 10:28:47 lee-desktop kernel: [    3.780063] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0x9
Sep 18 10:28:47 lee-desktop kernel: [    3.780064] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xb
Sep 18 10:28:47 lee-desktop kernel: [    3.780066] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xd
Sep 18 10:28:47 lee-desktop kernel: [    3.780067] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0xf
Sep 18 10:28:47 lee-desktop kernel: [    3.780068] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x11
Sep 18 10:28:47 lee-desktop kernel: [    3.780069] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x11
Sep 18 10:28:47 lee-desktop kernel: [    3.780071] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
Sep 18 10:28:47 lee-desktop kernel: [    3.780232] registered taskstats version 1
Sep 18 10:28:47 lee-desktop kernel: [    3.780348]   Magic number: 9:101:492
Sep 18 10:28:47 lee-desktop kernel: [    3.780436] rtc_cmos 00:03: setting system clock to 2009-09-18 17:28:40 UTC (1253294920)
Sep 18 10:28:47 lee-desktop kernel: [    3.780438] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 18 10:28:47 lee-desktop kernel: [    3.780439] EDD information not available.
Sep 18 10:28:47 lee-desktop kernel: [    3.780470] Freeing unused kernel memory: 532k freed
Sep 18 10:28:47 lee-desktop kernel: [    3.780676] Write protecting the kernel read-only data: 6688k
Sep 18 10:28:47 lee-desktop kernel: [    3.888657] usb 4-3: new low speed USB device using ohci_hcd and address 2
Sep 18 10:28:47 lee-desktop kernel: [    3.942223] ohci1394 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 18 10:28:47 lee-desktop kernel: [    3.994102] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fbdff800-fbdfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 18 10:28:47 lee-desktop kernel: [    4.036052] FDC 0 is a post-1991 82077
Sep 18 10:28:47 lee-desktop kernel: [    4.037896] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep 18 10:28:47 lee-desktop kernel: [    4.037916] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 10:28:47 lee-desktop kernel: [    4.038412] eth0: RTL8168c/8111c at 0xffffc2000006a000, 00:24:8c:69:66:e9, XID 3c4000c0 IRQ 2299
Sep 18 10:28:47 lee-desktop kernel: [    4.057299] usb 4-3: configuration #1 chosen from 1 choice
Sep 18 10:28:47 lee-desktop kernel: [    4.283980] usbcore: registered new interface driver hiddev
Sep 18 10:28:47 lee-desktop kernel: [    4.284161] usbcore: registered new interface driver usbhid
Sep 18 10:28:47 lee-desktop kernel: [    4.284163] usbhid: v2.6:USB HID core driver
Sep 18 10:28:47 lee-desktop kernel: [    4.295506] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input3
Sep 18 10:28:47 lee-desktop kernel: [    4.324085] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-3/input0
Sep 18 10:28:47 lee-desktop kernel: [    4.331248] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
Sep 18 10:28:47 lee-desktop kernel: [    4.331973] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input4
Sep 18 10:28:47 lee-desktop kernel: [    4.372123] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-3/input1
Sep 18 10:28:47 lee-desktop kernel: [    4.498402] PM: Starting manual resume from disk
Sep 18 10:28:47 lee-desktop kernel: [    4.508159] EXT4-fs: barriers enabled
Sep 18 10:28:47 lee-desktop kernel: [    4.514174] kjournald2 starting.  Commit interval 5 seconds
Sep 18 10:28:47 lee-desktop kernel: [    4.514183] EXT4-fs: delayed allocation enabled
Sep 18 10:28:47 lee-desktop kernel: [    4.514184] EXT4-fs: file extents enabled
Sep 18 10:28:47 lee-desktop kernel: [    4.514790] EXT4-fs: mballoc enabled
Sep 18 10:28:47 lee-desktop kernel: [    4.514793] EXT4-fs: mounted filesystem with ordered data mode.
Sep 18 10:28:47 lee-desktop kernel: [    7.274365] udev: starting version 141
Sep 18 10:28:47 lee-desktop kernel: [    7.659789] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Sep 18 10:28:47 lee-desktop kernel: [    7.673286] [fglrx] Maximum main memory to use for locked dma buffers: 3739 MBytes.
Sep 18 10:28:47 lee-desktop kernel: [    7.673415] [fglrx]   vendor: 1002 device: 9442 count: 1
Sep 18 10:28:47 lee-desktop kernel: [    7.673632] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
Sep 18 10:28:47 lee-desktop kernel: [    7.673643] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 18 10:28:47 lee-desktop kernel: [    7.673997] [fglrx] Driver built-in PAT support is enabled successfully
Sep 18 10:28:47 lee-desktop kernel: [    7.674030] [fglrx] module loaded - fglrx 8.65.4 [Aug 13 2009] with 1 minors
Sep 18 10:28:47 lee-desktop kernel: [    7.828667] input: PC Speaker as /devices/platform/pcspkr/input/input5
Sep 18 10:28:47 lee-desktop kernel: [    7.842690] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Sep 18 10:28:47 lee-desktop kernel: [    7.870395] parport_pc 00:07: reported by Plug and Play ACPI
Sep 18 10:28:47 lee-desktop kernel: [    7.870453] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 18 10:28:47 lee-desktop kernel: [    7.919635] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
Sep 18 10:28:47 lee-desktop kernel: [    7.919638] ACPI: Device needs an ACPI driver
Sep 18 10:28:47 lee-desktop kernel: [    7.919645] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Sep 18 10:28:47 lee-desktop kernel: [    7.966864] ppdev: user-space parallel port driver
Sep 18 10:28:47 lee-desktop kernel: [    8.012943] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Sep 18 10:28:47 lee-desktop kernel: [    8.013730] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Sep 18 10:28:47 lee-desktop kernel: [    8.013977] ndiswrapper 0000:04:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Sep 18 10:28:47 lee-desktop kernel: [    8.014993] ndiswrapper: using IRQ 21
Sep 18 10:28:47 lee-desktop kernel: [    8.058948] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 18 10:28:47 lee-desktop kernel: [    8.119642] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 18 10:28:47 lee-desktop kernel: [    8.268730] wlan0: ethernet device 00:22:3f:de:e8:55 using NDIS driver: wg311v3, version: 0x3010004, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
Sep 18 10:28:47 lee-desktop kernel: [    8.268745] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Sep 18 10:28:47 lee-desktop kernel: [    8.268872] usbcore: registered new interface driver ndiswrapper
Sep 18 10:28:47 lee-desktop kernel: [    8.396559] lp0: using parport0 (interrupt-driven).
Sep 18 10:28:47 lee-desktop kernel: [    8.416910] it87: Found IT8712F chip at 0x290, revision 8
Sep 18 10:28:47 lee-desktop kernel: [    8.416919] it87: in3 is VCC (+5V)
Sep 18 10:28:47 lee-desktop kernel: [    8.416920] it87: in7 is VCCH (+5V Stand-By)
Sep 18 10:28:47 lee-desktop kernel: [    8.516739] Adding 7903972k swap on /dev/sda2.  Priority:-1 extents:1 across:7903972k
Sep 18 10:28:47 lee-desktop kernel: [    9.059353] EXT4 FS on sda1, internal journal on sda1:8
Sep 18 10:28:47 lee-desktop kernel: [    9.799017] EXT4-fs: barriers enabled
Sep 18 10:28:47 lee-desktop kernel: [    9.814009] kjournald2 starting.  Commit interval 5 seconds
Sep 18 10:28:47 lee-desktop kernel: [    9.814436] EXT4 FS on sda3, internal journal on sda3:8
Sep 18 10:28:47 lee-desktop kernel: [    9.814437] EXT4-fs: delayed allocation enabled
Sep 18 10:28:47 lee-desktop kernel: [    9.814438] EXT4-fs: file extents enabled
Sep 18 10:28:47 lee-desktop kernel: [    9.847354] EXT4-fs: mballoc enabled
Sep 18 10:28:47 lee-desktop kernel: [    9.847359] EXT4-fs: mounted filesystem with ordered data mode.
Sep 18 10:28:47 lee-desktop kernel: [   10.026171] type=1505 audit(1253294926.743:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2091
Sep 18 10:28:47 lee-desktop kernel: [   10.061244] type=1505 audit(1253294926.779:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2095
Sep 18 10:28:47 lee-desktop kernel: [   10.061361] type=1505 audit(1253294926.779:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2095
Sep 18 10:28:47 lee-desktop kernel: [   10.061396] type=1505 audit(1253294926.779:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2095
Sep 18 10:28:47 lee-desktop kernel: [   10.061427] type=1505 audit(1253294926.779:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2095
Sep 18 10:28:47 lee-desktop kernel: [   10.158743] type=1505 audit(1253294926.875:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2100
Sep 18 10:28:47 lee-desktop kernel: [   10.158884] type=1505 audit(1253294926.875:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2100
Sep 18 10:28:47 lee-desktop kernel: [   10.182679] type=1505 audit(1253294926.899:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2104
Sep 18 10:28:48 lee-desktop kernel: [   12.201708] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 18 10:28:48 lee-desktop kernel: [   12.201711] Bluetooth: BNEP filters: protocol multicast
Sep 18 10:28:48 lee-desktop kernel: [   12.250823] Bridge firewalling registered
Sep 18 10:28:50 lee-desktop kernel: [   13.808073] [fglrx] Firegl kernel thread PID: 2867
Sep 18 10:28:51 lee-desktop kernel: [   15.044201] [fglrx] Gart USWC size:1217 M.
Sep 18 10:28:51 lee-desktop kernel: [   15.044204] [fglrx] Gart cacheable size:483 M.
Sep 18 10:28:51 lee-desktop kernel: [   15.044209] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep 18 10:28:51 lee-desktop kernel: [   15.044211] [fglrx] Reserved FB block: Unshared offset:fc2f000, size:3d1000 
Sep 18 10:28:51 lee-desktop kernel: [   15.044213] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
Sep 18 10:28:54 lee-desktop kernel: [   17.281892] r8169: eth0: link down
Sep 18 10:28:54 lee-desktop kernel: [   17.282518] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 18 10:28:56 lee-desktop kernel: [   19.280581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 18 10:29:16 lee-desktop kernel: [   39.940370] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 18 10:29:53 lee-desktop kernel: [   77.000303] Clocksource tsc unstable (delta = -328053485 ns)
Sep 18 10:48:47 lee-desktop -- MARK --
Sep 18 11:08:21 lee-desktop kernel: [ 2384.638711] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:09:22 lee-desktop kernel: [ 2445.485949] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:10:23 lee-desktop kernel: [ 2506.308864] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:11:23 lee-desktop kernel: [ 2566.773753] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:12:24 lee-desktop kernel: [ 2627.523275] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:13:24 lee-desktop kernel: [ 2687.579860] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:14:24 lee-desktop kernel: [ 2748.031962] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:15:25 lee-desktop kernel: [ 2808.553541] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:16:25 lee-desktop kernel: [ 2868.694744] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:17:28 lee-desktop kernel: [ 2931.512934] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:18:28 lee-desktop kernel: [ 2992.113224] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:19:32 lee-desktop kernel: [ 3055.694131] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:20:32 lee-desktop kernel: [ 3115.764413] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:21:32 lee-desktop kernel: [ 3176.132141] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:22:34 lee-desktop kernel: [ 3237.788485] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:23:36 lee-desktop kernel: [ 3299.607301] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:24:37 lee-desktop kernel: [ 3360.777370] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:25:37 lee-desktop kernel: [ 3421.175875] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:26:38 lee-desktop kernel: [ 3481.958663] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:27:38 lee-desktop kernel: [ 3542.257658] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:28:39 lee-desktop kernel: [ 3602.787761] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:29:39 lee-desktop kernel: [ 3662.873161] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:30:40 lee-desktop kernel: [ 3723.773443] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:31:40 lee-desktop kernel: [ 3783.811088] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:32:40 lee-desktop kernel: [ 3843.920589] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:33:40 lee-desktop kernel: [ 3904.046998] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:34:41 lee-desktop kernel: [ 3964.410284] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:35:42 lee-desktop kernel: [ 4025.702681] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:36:43 lee-desktop kernel: [ 4086.558812] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:37:45 lee-desktop kernel: [ 4149.163213] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:38:50 lee-desktop kernel: [ 4213.659922] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:39:50 lee-desktop kernel: [ 4273.683505] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:40:55 lee-desktop kernel: [ 4338.506731] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:41:59 lee-desktop kernel: [ 4402.783899] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:43:02 lee-desktop kernel: [ 4465.922964] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:44:09 lee-desktop kernel: [ 4532.821217] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:45:09 lee-desktop kernel: [ 4592.938040] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:46:09 lee-desktop kernel: [ 4652.953624] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:47:10 lee-desktop kernel: [ 4714.218655] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:48:12 lee-desktop kernel: [ 4775.343733] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:49:12 lee-desktop kernel: [ 4835.522887] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:50:16 lee-desktop kernel: [ 4900.022822] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:51:17 lee-desktop kernel: [ 4960.284579] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:52:17 lee-desktop kernel: [ 5020.480766] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:53:17 lee-desktop kernel: [ 5080.545296] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:54:17 lee-desktop kernel: [ 5140.766024] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:55:17 lee-desktop kernel: [ 5200.927332] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:56:17 lee-desktop kernel: [ 5260.953376] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:57:18 lee-desktop kernel: [ 5321.489151] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:58:18 lee-desktop kernel: [ 5381.751789] possible SYN flooding on port 51724. Sending cookies.
Sep 18 11:59:18 lee-desktop kernel: [ 5441.884697] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:00:19 lee-desktop kernel: [ 5503.221878] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:01:23 lee-desktop kernel: [ 5567.039273] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:02:24 lee-desktop kernel: [ 5627.468895] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:03:26 lee-desktop kernel: [ 5690.169582] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:04:27 lee-desktop kernel: [ 5750.937339] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:05:27 lee-desktop kernel: [ 5810.962591] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:06:28 lee-desktop kernel: [ 5871.570097] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:07:28 lee-desktop kernel: [ 5931.666874] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:08:28 lee-desktop kernel: [ 5991.751330] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:09:28 lee-desktop kernel: [ 6052.090601] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:10:29 lee-desktop kernel: [ 6112.991337] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:11:32 lee-desktop kernel: [ 6175.326232] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:12:32 lee-desktop kernel: [ 6235.448039] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:13:32 lee-desktop kernel: [ 6295.879276] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:14:33 lee-desktop kernel: [ 6356.922539] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:15:34 lee-desktop kernel: [ 6417.482620] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:16:35 lee-desktop kernel: [ 6478.430400] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:17:37 lee-desktop kernel: [ 6540.546729] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:18:38 lee-desktop kernel: [ 6601.328194] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:19:38 lee-desktop kernel: [ 6661.440555] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:20:38 lee-desktop kernel: [ 6722.013438] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:21:39 lee-desktop kernel: [ 6782.604340] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:22:39 lee-desktop kernel: [ 6843.115724] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:23:40 lee-desktop kernel: [ 6903.485564] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:24:40 lee-desktop kernel: [ 6963.556022] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:25:40 lee-desktop kernel: [ 7024.233568] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:26:42 lee-desktop kernel: [ 7085.637395] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:27:43 lee-desktop kernel: [ 7146.707155] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:28:44 lee-desktop kernel: [ 7207.666666] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:29:44 lee-desktop kernel: [ 7267.686352] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:30:44 lee-desktop kernel: [ 7327.879619] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:31:44 lee-desktop kernel: [ 7387.963656] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:32:44 lee-desktop kernel: [ 7447.996843] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:33:45 lee-desktop kernel: [ 7508.328658] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:34:45 lee-desktop kernel: [ 7568.535550] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:35:45 lee-desktop kernel: [ 7628.652254] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:36:45 lee-desktop kernel: [ 7688.858007] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:37:45 lee-desktop kernel: [ 7748.998843] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:38:45 lee-desktop kernel: [ 7809.186473] possible SYN flooding on port 51724. Sending cookies.
Sep 18 12:47:51 lee-desktop kernel: [ 8354.925375] npviewer.bin[13751]: segfault at f1a7311c ip 00000000f1a7311c sp 00000000ffbbe534 error 14
Sep 18 13:08:47 lee-desktop -- MARK --
Sep 18 13:28:47 lee-desktop -- MARK --
Sep 18 13:43:01 lee-desktop kernel: [11664.923185] npviewer.bin[15306]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffa37210 error 14
Sep 18 14:08:47 lee-desktop -- MARK --
Sep 18 14:19:19 lee-desktop syslogd 1.5.0#5ubuntu3: restart.
Sep 18 14:19:19 lee-desktop kernel: Inspecting /boot/System.map-2.6.28-15-generic
Sep 18 14:19:19 lee-desktop kernel: Cannot find map file.
```

---

### Post by hal10000 on 2009-09-19
There is a kernel message
> Sep 18 11:08:21 lee-desktop kernel: [ 2384.638711] possible SYN flooding on port 51724. Sending cookies.

which starts at 11:08 and is repeated very often. Can you remember what you did at that time? Did you perhaps start a bittorrent tool like azureus (vuze) or ktorrent or something similar at that time?

This message means, that your linux-kernel and your firewall thinks that your system is under a DOS-Attack (Denial of service attack).

If you started a bittorrent tool then you don't have to fear, because bittorrent-clients often causes the kernl to think it's a DOS-Attack. 
But if the torrent-tool you started was azureus (vuze), then i can tell you that on my system a once had also lock ups like you when i started an older version of azureus and after i upgraded the version this behaviour disappeared.
So i suggest stop your torrent-tool and look if you have a stable system for a few days. Then try to get another version or another torrent-program.

I'm not too experienced in these things, but in case the above mentioned kernel message has nothing to do with a bittorrent tool, then it is possible that you are really under attack. But i don't know if the attacker can cause your system to hang up.

---

### Post by DeMus on 2009-09-19
> **LeeLgrqst said:**
> I have Ubuntu 9.04 64

My computer will lock up, and I won't be able to do anything.  I have to hit the reset button to get it working again.  Then sometimes it does it again in just a few minutes, other times it will go a day or two.  

I have no idea where to start to solve this problem, except for here.  This is also a computer I built myself, and I am by no means any kind of expert.

Here is a short list of what I have:
Motherboard: M3a78-EM
CPU:         AMD Athlon x2 - 5600
Video:       Radeon HD4850
Wireless:    wg311v3

Also, not sure if its related, but many times I get black boxes in whatever window I'm working in.  I included an example of what I'm talking about.  I followed the directions on the first link to a T (first link), when I installed the driver for the video card.

This is a fresh install, and I followed many of the directions given in the second link to complete my installation.

I also get a message during boot up that I can't read cause it goes away too fast.  Not sure if that is related either.  Just trying to provide you with as much relevant information as possible.

My main concern is to make the computer stop locking up.  If the display is an unrelated issue, I'll work on that some other time.  I just don't want to have to reset my computer all the time any more.  Thanks.

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

[http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/)

Do you use Compiz? If so uninstall it and set your effects to None. I did, after some strange things I got and they were gone instantly.

---

### Post by LeeLgrqst on 2009-09-19
I noticed a lot of those lines too, and suspected the bittorrent program.

I am using Deluge.  I was using it on my laptop without any problems for a long time.  I will not use it and see if the system locks up again.  If it does, I will post the information from that file.

Compiz is installed and running.  Again, on the laptop it worked perfectly, without any problems.  I would prefer to keep using it, and figure out what exactly the problem is, and fix it.  

Thank you so much for the help, when I have more information about what is going on, I will share it with you.  

I am thinking the black spots on the windows is a unrelated issue and that I should make a separate thread for it.

---

