---
title: "constantly crashing!"
date: 2010-02-14
forum: General Help
---

### Post by planesinspace on 2010-02-14
I have just installed Ubuntu 9.10 on my Dell Inspiron 9400 Laptop, and I am finding that it is constantly freezing on me, and I have to restart.
Does anyone have any advice? I have Windows Vista on my computer as well which runs perfectly.
 
Any help much appreciated!

---

### Post by Richard1979 on 2010-02-14
If there anything related to this in the syslog?

Do a "tail -n 50 /var/log/messages" and post it here.

BTW if you don't know, you need to do this in the Terminal so go to Applications > Accessories > Terminal.
You can highlight text like in Windows and right click and copy/paste etc.

---

### Post by planesinspace on 2010-02-14
This is what it prints:
 
 
[EMAIL="tash@ubuntu:~$"]tash@ubuntu:~$[/EMAIL] tail -n 50 /var/log/messages
Feb 14 18:22:24 ubuntu kernel: [   12.144344] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Feb 14 18:22:24 ubuntu kernel: [   12.144362] ricoh-mmc: Controller is now disabled.
Feb 14 18:22:24 ubuntu kernel: [   12.167669] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Feb 14 18:22:24 ubuntu kernel: [   12.209431] cfg80211: World regulatory domain updated:
Feb 14 18:22:24 ubuntu kernel: [   12.209435]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 18:22:24 ubuntu kernel: [   12.209438]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 14 18:22:24 ubuntu kernel: [   12.209440]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 14 18:22:24 ubuntu kernel: [   12.209443]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 14 18:22:24 ubuntu kernel: [   12.209445]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 14 18:22:24 ubuntu kernel: [   12.209448]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 14 18:22:24 ubuntu kernel: [   12.326016] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
Feb 14 18:22:24 ubuntu kernel: [   12.326051] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Feb 14 18:22:24 ubuntu kernel: [   12.328114] Registered led device: mmc0::
Feb 14 18:22:24 ubuntu kernel: [   12.329149] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Feb 14 18:22:24 ubuntu kernel: [   12.396145] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 14 18:22:24 ubuntu kernel: [   12.624572] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Feb 14 18:22:24 ubuntu kernel: [   12.624658] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Feb 14 18:22:24 ubuntu kernel: [   13.780264] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Feb 14 18:22:24 ubuntu kernel: [   13.780268] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Feb 14 18:22:24 ubuntu kernel: [   13.780392] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 14 18:22:24 ubuntu kernel: [   13.850016] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 4 802.11a channels
Feb 14 18:22:24 ubuntu kernel: [   13.850020] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
Feb 14 18:22:24 ubuntu kernel: [   25.433970] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
Feb 14 18:22:24 ubuntu kernel: [   25.490211] EXT4-fs (loop0): internal journal on loop0:8
Feb 14 18:22:24 ubuntu kernel: [   25.782239] __ratelimit: 3 callbacks suppressed
Feb 14 18:22:24 ubuntu kernel: [   25.782243] type=1505 audit(1266189744.348:12): operation="profile_replace" pid=939 name=/usr/share/gdm/guest-session/Xsession
Feb 14 18:22:24 ubuntu kernel: [   25.787265] type=1505 audit(1266189744.352:13): operation="profile_replace" pid=940 name=/sbin/dhclient3
Feb 14 18:22:24 ubuntu kernel: [   25.788025] type=1505 audit(1266189744.352:14): operation="profile_replace" pid=940 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 14 18:22:24 ubuntu kernel: [   25.788428] type=1505 audit(1266189744.356:15): operation="profile_replace" pid=940 name=/usr/lib/connman/scripts/dhclient-script
Feb 14 18:22:24 ubuntu kernel: [   25.792146] type=1505 audit(1266189744.360:16): operation="profile_replace" pid=942 name=/usr/bin/evince
Feb 14 18:22:24 ubuntu kernel: [   25.803490] type=1505 audit(1266189744.368:17): operation="profile_replace" pid=942 name=/usr/bin/evince-previewer
Feb 14 18:22:24 ubuntu kernel: [   25.810197] type=1505 audit(1266189744.376:18): operation="profile_replace" pid=942 name=/usr/bin/evince-thumbnailer
Feb 14 18:22:24 ubuntu kernel: [   25.819451] type=1505 audit(1266189744.384:19): operation="profile_replace" pid=944 name=/usr/lib/cups/backend/cups-pdf
Feb 14 18:22:24 ubuntu kernel: [   25.820339] type=1505 audit(1266189744.388:20): operation="profile_replace" pid=944 name=/usr/sbin/cupsd
Feb 14 18:22:24 ubuntu kernel: [   25.822762] type=1505 audit(1266189744.388:21): operation="profile_replace" pid=945 name=/usr/sbin/tcpdump
Feb 14 18:22:24 ubuntu kernel: [   26.108356] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
Feb 14 18:22:24 ubuntu kernel: [   26.213711] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
Feb 14 18:22:24 ubuntu kernel: [   26.331236] Registered led device: iwl-phy0::radio
Feb 14 18:22:24 ubuntu kernel: [   26.331257] Registered led device: iwl-phy0::assoc
Feb 14 18:22:24 ubuntu kernel: [   26.331314] Registered led device: iwl-phy0::RX
Feb 14 18:22:24 ubuntu kernel: [   26.331331] Registered led device: iwl-phy0::TX
Feb 14 18:22:24 ubuntu kernel: [   26.349910] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 14 18:22:24 ubuntu kernel: [   26.354910] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 14 18:22:25 ubuntu kernel: [   26.558403] ppdev: user-space parallel port driver
Feb 14 18:22:26 ubuntu kernel: [   27.909732] [drm] Setting GART location based on new memory map
Feb 14 18:22:26 ubuntu kernel: [   27.911825] [drm] Loading R500 Microcode
Feb 14 18:22:26 ubuntu kernel: [   27.911879] [drm] Num pipes: 1
Feb 14 18:22:26 ubuntu kernel: [   27.911893] [drm] writeback test succeeded in 1 usecs
Feb 14 18:22:38 ubuntu kernel: [   39.986637] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 14 18:22:38 ubuntu kernel: [   39.987361] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2009/07/14 04:29 (1ed4)

---

### Post by Richard1979 on 2010-02-14
I'm guessing the UDF mount is a CD/DVD you have in the drive or a 3G broadband USB stick or something.

Does this laptop get an IP address? Is it using wireless or can you plug an ethernet cable in?
The freezing might be due to it waiting for an IP address from your router via DHCP.
It's a long shot, but I've seen servers sit waiting for an IP for ages before.

It's this line which makes me think something is up with your network:
Feb 14 18:22:24 ubuntu kernel: [   26.354910] ADDRCONF(NETDEV_UP): eth0: link is not ready

Try plugging an ethernet cable directly into it and reboot.

---

### Post by planesinspace on 2010-02-14
I'm not sure how to check the IP address?
 
Well the internet is actually not working on my Ubuntu at the moment ( I also have this post at the moment regardinhg that: [http://ubuntuforums.org/showthread.php?t=1403900](http://ubuntuforums.org/showthread.php?t=1403900)), but yes it is a 3G USB stick/modem that doesn't seem to be able to get connected. Are you saying its the internet thing that could be causing the crashing? Because I think it was freezing even when I didnt have the 3G USB in.

---

