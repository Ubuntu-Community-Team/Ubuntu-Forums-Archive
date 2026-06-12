---
title: "Read-only Filesystem on Boot"
date: 2011-03-15
forum: General Help
---

### Post by 00000 on 2011-03-15
About 1/3 to 1/2 the time I boot my Ubuntu machine I discover that my root filesystem is mounted read-only.  Then I reboot to see that it's checking my filesystem for errors, after which it reboots yet a third time.  This has been happening off and on for several months.

I'm not sure yet if this has caused any kind of filesystem corruption.  The disk utility reports no physical disk errors.

I can't seem to find this specific problem on the forum anywhere (I may not be searching with the right keywords)...  Does anyone else have this problem, or know a fix for it?  I'm running Maverick 64-bit.  Here are some log file exerpts, which shows the filesystem being mounted read-only (I think)...  I'm not sure what else would be useful to post.

> Mar 14 09:28:40 fred kernel: [    3.841282] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 14 09:28:40 fred kernel: [    3.843534] ata4.00: ATAPI: TOSHIBA DVD/HD  SD-H802A, HP10, max UDMA/33
Mar 14 09:28:40 fred kernel: [    3.843545] ata4.00: applying bridge limits
Mar 14 09:28:40 fred kernel: [    3.845803] ata4.00: configured for UDMA/33
Mar 14 09:28:40 fred kernel: [    3.860976] scsi 3:0:0:0: CD-ROM            TOSHIBA  DVD/HD  SD-H802A HP10 PQ: 0 ANSI: 5
Mar 14 09:28:40 fred kernel: [    3.863120] sr1: scsi3-mmc drive: 15x/15x cd/rw xa/form2 cdda tray
Mar 14 09:28:40 fred kernel: [    3.863317] sr 3:0:0:0: Attached scsi generic sg3 type 5
Mar 14 09:28:40 fred kernel: [    4.222543] ata5: SATA link down (SStatus 0 SControl 300)
Mar 14 09:28:40 fred kernel: [    4.390208] Initializing USB Mass Storage driver...
Mar 14 09:28:40 fred kernel: [    4.390367] scsi6 : usb-storage 2-5.2:1.0
Mar 14 09:28:40 fred kernel: [    4.390475] usbcore: registered new interface driver usb-storage
Mar 14 09:28:40 fred kernel: [    4.390477] USB Mass Storage support registered.
Mar 14 09:28:40 fred kernel: [    4.593790] ata6: SATA link down (SStatus 0 SControl 300)
Mar 14 09:28:40 fred kernel: [    4.900268] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Mar 14 09:28:40 fred kernel: [    5.400480] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
Mar 14 09:28:40 fred kernel: [    5.406717] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
Mar 14 09:28:40 fred kernel: [    5.412976] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
Mar 14 09:28:40 fred kernel: [    5.419222] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
Mar 14 09:28:40 fred kernel: [    5.419804] sd 6:0:0:0: Attached scsi generic sg4 type 0
Mar 14 09:28:40 fred kernel: [    5.419969] sd 6:0:0:1: Attached scsi generic sg5 type 0
Mar 14 09:28:40 fred kernel: [    5.420139] sd 6:0:0:2: Attached scsi generic sg6 type 0
Mar 14 09:28:40 fred kernel: [    5.420289] sd 6:0:0:3: Attached scsi generic sg7 type 0
Mar 14 09:28:40 fred kernel: [    5.423584] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Mar 14 09:28:40 fred kernel: [    5.424331] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Mar 14 09:28:40 fred kernel: [    5.425079] sd 6:0:0:2: [sde] Attached SCSI removable disk
Mar 14 09:28:40 fred kernel: [    5.425826] sd 6:0:0:3: [sdf] Attached SCSI removable disk
Mar 14 09:28:40 fred kernel: [   21.592123] udev[393]: starting version 163...

> Mar 14 09:28:40 fred kernel: [   22.652195] udev[410]: renamed network interface wlan0 to wlan1
Mar 14 09:28:40 fred kernel: [   22.686750] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 14 09:28:40 fred kernel: [   22.700684] Hammerfall-DSP: loading firmware
Mar 14 09:28:40 fred kernel: [   22.854946] type=1400 audit(1300112920.321:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1022 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   22.855055] type=1400 audit(1300112920.321:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1023 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   22.855661] type=1400 audit(1300112920.321:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1023 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   22.855995] type=1400 audit(1300112920.321:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1023 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   22.856935] type=1400 audit(1300112920.321:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1027 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   22.858641] type=1400 audit(1300112920.321:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1026 comm="apparmor_parser"
Mar 14 09:28:40 fred kernel: [   23.070870] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Mar 14 09:28:43 fred kernel: [   26.000037] Hammerfall-DSP: finished firmware loading
Mar 14 09:28:45 fred kernel: [   28.386968] ppdev: user-space parallel port driver
Mar 14 09:28:46 fred kernel: [   29.165187] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar 14 09:28:49 fred pulseaudio[1625]: lock-autospawn.c: Cannot access autospawn lock....

> Mar 14 09:35:10 fred kernel: [   22.864747] udev[408]: renamed network interface wlan0 to wlan1
Mar 14 09:35:10 fred kernel: [   22.911098] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 14 09:35:10 fred kernel: [   22.981304] usbcore: registered new interface driver snd-usb-audio
Mar 14 09:35:10 fred kernel: [   23.036485] type=1400 audit(1300113310.511:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1021 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.036490] type=1400 audit(1300113310.511:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1020 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.037105] type=1400 audit(1300113310.511:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1021 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.037438] type=1400 audit(1300113310.511:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1021 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.038206] type=1400 audit(1300113310.511:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1025 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.038947] type=1400 audit(1300113310.511:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1025 comm="apparmor_parser"
Mar 14 09:35:10 fred kernel: [   23.076785] ppdev: user-space parallel port driver
Mar 14 09:35:10 fred kernel: [   23.162058] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Mar 14 09:35:13 fred kernel: [   25.772533] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Mar 14 09:35:13 fred kernel: [   26.334427] Intel AES-NI instructions are not detected.
Mar 14 09:35:13 fred kernel: [   26.364784] padlock: VIA PadLock not detected.
Mar 14 09:35:14 fred kernel: [   26.558125] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar 14 09:35:15 fred kernel: [   27.892977] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar 14 09:35:15 fred pulseaudio[1812]: lock-autospawn.c: Cannot access autospawn lock.
Mar 14 09:35:20 fred pulseaudio[1756]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1e.0/0000:01:00.0/sound/card0 (alsa_card.pci-0000_01_00.0) more often than 5 times in 10s
Mar 14 09:35:39 fred pulseaudio[1756]: ratelimit.c: 1 events suppressed
Mar 14 09:35:39 fred pulseaudio[1756]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1e.0/0000:01:00.0/sound/card0 (alsa_card.pci-0000_01_00.0) more often than 5 times in 10s
Mar 14 09:36:10 fred pulseaudio[1756]: last message repeated 2 times
Mar 14 09:36:24 fred pulseaudio[2358]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1e.0/0000:01:00.0/sound/card0 (alsa_card.pci-0000_01_00.0) more often than 5 times in 10s
Mar 14 10:03:00 fred kernel: [ 1693.185770] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
Mar 14 10:03:00 fred kernel: [ 1693.189684] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Mar 14 10:04:05 fred rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="969" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

---

