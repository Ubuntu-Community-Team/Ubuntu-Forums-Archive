---
title: "configuring logrotate"
date: 2009-11-22
forum: General Help
---

### Post by anti-destin on 2009-11-22
here's the problem. for some reason, my log files (in particular, kern.log, syslog, and messages) grow rapidly rather unpredictably, sometimes reaching several hundred mb within a day or two. i didn't notice the problem until last week each grew to around 1.6gb.

when they get that large, i can't view the contents, so i don't know why they're growing so quickly. but when they're fairly small, they seem unremarkable.

i read about logrotate and have configured it according to my needs. but it doesn't seem to be running automatically.

how can i configure when logrotate runs? could i make it run on shutdown, for example?

thanks.

---

### Post by dcstar on 2009-11-23
> **anti-destin said:**
> here's the problem. for some reason, my log files (in particular, kern.log, syslog, and messages) grow rapidly rather unpredictably, sometimes reaching several hundred mb within a day or two. i didn't notice the problem until last week each grew to around 1.6gb.

when they get that large, i can't view the contents, so i don't know why they're growing so quickly. but when they're fairly small, they seem unremarkable.

i read about logrotate and have configured it according to my needs. but it doesn't seem to be running automatically.

how can i configure when logrotate runs? could i make it run on shutdown, for example?

thanks.

```
man logrotate
```

---

### Post by anti-destin on 2009-11-23
thanks for the reply. but that simply tells me (unless i missed something) how to configure the rotation of the log files. i didn't see anything in there about specifying when logrotate itself should be called.

from what i can tell, logrotate is supposed to be called daily by cron, but i have no idea when it is called. 12am? 7pm? i was wondering whether it would be possible to specify the time or maybe have it run on certain events, e.g., shutdown.

if that's not possible, could i simply create a shutdown script?

---

### Post by HermanAB on 2009-11-23
Howdy,

You have to fix the problem of course, but it seems the symptom needs to be addressed first.  Stop the syslogd service (something like sudo service syslog stop, or even sudo killall syslogd). That will prevent the logs from growing.  Then read the old logs to figure out what is going on - you should not be getting so many log messages.

BTW, cron.daily runs things at 1 minute past 4am.

---

### Post by anti-destin on 2009-11-23
here's part of syslog:

```
Nov 23 09:50:49 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="778" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 23 09:50:50 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="778" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 23 09:51:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 09:53:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 09:55:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 09:55:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 09:55:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 09:55:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 09:55:36 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 23 09:55:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 09:56:12 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 09:56:12 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 09:57:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 09:59:02 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 09:59:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 09:59:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 09:59:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 09:59:33 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 09:59:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 23 09:59:54 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 10:00:03 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:00:03 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:00:08 ubuntu wpa_supplicant[1069]: WPA: Group rekeying completed with 00:1d:7e:be:a2:cb [GTK=CCMP]
Nov 23 10:00:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov 23 10:00:08 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 10:01:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:03:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:03:44 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 10:03:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 10:03:54 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 10:04:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 10:04:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 23 10:04:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:04:45 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:04:45 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:05:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:07:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:09:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:11:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:11:33 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:11:41 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 10:11:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 23 10:12:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:12:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 10:12:34 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:12:34 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:13:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:15:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:17:01 ubuntu CRON[1526]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 23 10:17:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:19:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:19:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 10:19:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 10:20:02 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 10:20:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 10:20:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 23 10:20:40 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 10:20:57 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:20:57 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:21:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:23:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:25:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:26:05 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 10:26:10 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 10:26:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 10:26:34 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 10:26:45 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 10:26:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:27:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 10:27:06 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:27:06 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:27:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:29:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:31:17 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:31:24 ubuntu NetworkManager: <info>  Sleeping...
Nov 23 10:31:24 ubuntu NetworkManager: <info>  (wlan0): now unmanaged
Nov 23 10:31:24 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Nov 23 10:31:24 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Nov 23 10:31:25 ubuntu NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1299
Nov 23 10:31:25 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov 23 10:31:25 ubuntu NetworkManager: <info>  (wlan0): cleaning up...
Nov 23 10:31:25 ubuntu NetworkManager: <info>  (wlan0): taking down device.
Nov 23 10:31:25 ubuntu kernel: [ 3469.322557] wlan0: deauthenticating by local choice (reason=3)
Nov 23 10:31:25 ubuntu kernel: [ 3469.466395] wlan0: disassociating by local choice (reason=3)
Nov 23 10:31:25 ubuntu kernel: [ 3470.130185] [drm] Num pipes: 1
Nov 23 10:36:43 ubuntu kernel: [ 3471.981160] PM: Syncing filesystems ... done.
Nov 23 10:36:43 ubuntu bluetoothd[905]: Stopping security manager 0
Nov 23 10:36:43 ubuntu kernel: [ 3471.983107] PM: Preparing system for mem sleep
Nov 23 10:36:43 ubuntu kernel: [ 3471.983112] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov 23 10:36:43 ubuntu bluetoothd[905]: HCI dev 0 down
Nov 23 10:36:43 ubuntu kernel: [ 3471.983889] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov 23 10:36:43 ubuntu kernel: [ 3471.983928] PM: Entering mem sleep
Nov 23 10:36:43 ubuntu bluetoothd[905]: Adapter /org/bluez/895/hci0 has been disabled
Nov 23 10:36:43 ubuntu kernel: [ 3471.983945] Suspending console(s) (use no_console_suspend to debug)
Nov 23 10:36:43 ubuntu kernel: [ 3472.051027] btusb_bulk_complete: hci0 urb ffff88006c0fd780 failed to resubmit (1)
Nov 23 10:36:43 ubuntu bluetoothd[905]: HCI dev 0 unregistered
Nov 23 10:36:43 ubuntu kernel: [ 3472.052018] btusb_bulk_complete: hci0 urb ffff88006c0fd300 failed to resubmit (1)
Nov 23 10:36:43 ubuntu kernel: [ 3472.053020] btusb_intr_complete: hci0 urb ffff88006c0fd6c0 failed to resubmit (1)
Nov 23 10:36:43 ubuntu bluetoothd[905]: Unregister path: /org/bluez/895/hci0
Nov 23 10:36:43 ubuntu kernel: [ 3472.110063] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 23 10:36:43 ubuntu kernel: [ 3472.110288] sd 0:0:0:0: [sda] Stopping disk
Nov 23 10:36:43 ubuntu kernel: [ 3473.533316] ACPI handle has no context!
Nov 23 10:36:43 ubuntu kernel: [ 3473.533403] ath5k 0000:08:00.0: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.550042] sky2 eth0: disabling interface
Nov 23 10:36:43 ubuntu kernel: [ 3473.550451] sky2 0000:02:00.0: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.680071] HDA Intel 0000:01:05.2: PCI INT B disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.680109] ACPI handle has no context!
Nov 23 10:36:43 ubuntu kernel: [ 3473.700039] pci 0000:01:05.0: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.810116] HDA Intel 0000:00:14.2: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830235] pata_atiixp 0000:00:14.1: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830245] ehci_hcd 0000:00:13.5: PCI INT D disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830254] ohci_hcd 0000:00:13.4: PCI INT C disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830263] ohci_hcd 0000:00:13.3: PCI INT B disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830271] ohci_hcd 0000:00:13.2: PCI INT C disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830279] ohci_hcd 0000:00:13.1: PCI INT B disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.830288] ohci_hcd 0000:00:13.0: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.910280] ahci 0000:00:12.0: PCI INT A disabled
Nov 23 10:36:43 ubuntu kernel: [ 3473.911526] PM: suspend devices took 1.930 seconds
Nov 23 10:36:43 ubuntu kernel: [ 3473.911712] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3474.150071] ACPI: Preparing to enter system sleep state S3
Nov 23 10:36:43 ubuntu kernel: [ 3474.150753] Disabling non-boot CPUs ...
Nov 23 10:36:43 ubuntu kernel: [ 3474.260022] CPU 1 is now offline
Nov 23 10:36:43 ubuntu kernel: [ 3474.260025] SMP alternatives: switching to UP code
Nov 23 10:36:43 ubuntu kernel: [ 3474.267643] CPU0 attaching NULL sched-domain.
Nov 23 10:36:43 ubuntu kernel: [ 3474.267647] CPU1 attaching NULL sched-domain.
Nov 23 10:36:43 ubuntu kernel: [ 3474.267658] CPU0 attaching NULL sched-domain.
Nov 23 10:36:43 ubuntu kernel: [ 3474.267870] CPU1 is down
Nov 23 10:36:43 ubuntu kernel: [ 3474.267879] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 23 10:36:43 ubuntu kernel: [ 3474.267879] Back to C!
Nov 23 10:36:43 ubuntu kernel: [ 3474.267879] CPU0: Thermal LVT vector (0xfa) already installed
Nov 23 10:36:43 ubuntu kernel: [ 3474.267879] Enabling non-boot CPUs ...
Nov 23 10:36:43 ubuntu kernel: [ 3474.267879] SMP alternatives: switching to SMP code
Nov 23 10:36:43 ubuntu kernel: [ 3474.275453] Booting processor 1 APIC 0x1 ip 0x6000
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] Initializing CPU#1
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] Calibrating delay using timer specific routine.. 3325.10 BogoMIPS (lpj=16625500)
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU: L2 cache: 2048K
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU 1/0x1 -> Node 0
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU: Physical Processor ID: 0
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU: Processor Core ID: 1
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] mce: CPU supports 6 MCE banks
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] CPU1: Thermal monitoring enabled (TM2)
Nov 23 10:36:43 ubuntu kernel: [ 3474.267483] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 23 10:36:43 ubuntu kernel: [ 3474.431794] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Nov 23 10:36:43 ubuntu kernel: [ 3474.431858] CPU0 attaching NULL sched-domain.
Nov 23 10:36:43 ubuntu kernel: [ 3474.432519] Switched to high resolution mode on CPU 1
Nov 23 10:36:43 ubuntu kernel: [ 3474.470026] CPU0 attaching sched-domain:
Nov 23 10:36:43 ubuntu kernel: [ 3474.470030]  domain 0: span 0-1 level MC
Nov 23 10:36:43 ubuntu kernel: [ 3474.470033]   groups: 0 1
Nov 23 10:36:43 ubuntu kernel: [ 3474.470038] CPU1 attaching sched-domain:
Nov 23 10:36:43 ubuntu kernel: [ 3474.470040]  domain 0: span 0-1 level MC
Nov 23 10:36:43 ubuntu kernel: [ 3474.470043]   groups: 1 0
Nov 23 10:36:43 ubuntu kernel: [ 3474.472519] CPU1 is up
Nov 23 10:36:43 ubuntu kernel: [ 3474.472522] ACPI: Waking up from system sleep state S3
Nov 23 10:36:43 ubuntu kernel: [ 3475.000015] Clocksource tsc unstable (delta = -500001867 ns)
Nov 23 10:36:43 ubuntu bluetoothd[905]: HCI dev 0 registered
Nov 23 10:36:43 ubuntu kernel: [ 3475.560185] pcieport-driver 0000:00:04.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560194] pcieport-driver 0000:00:04.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560199] pcieport-driver 0000:00:04.0: restoring config space at offset 0x8 (was 0x0, writing 0xf040f040)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560204] pcieport-driver 0000:00:04.0: restoring config space at offset 0x7 (was 0x101, writing 0xa1a1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560208] pcieport-driver 0000:00:04.0: restoring config space at offset 0x6 (was 0x0, writing 0x40200)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560214] pcieport-driver 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560220] pcieport-driver 0000:00:04.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560253] pcieport-driver 0000:00:06.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560261] pcieport-driver 0000:00:06.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560266] pcieport-driver 0000:00:06.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560270] pcieport-driver 0000:00:06.0: restoring config space at offset 0x7 (was 0x101, writing 0x1f1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560275] pcieport-driver 0000:00:06.0: restoring config space at offset 0x6 (was 0x0, writing 0x70500)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560281] pcieport-driver 0000:00:06.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560286] pcieport-driver 0000:00:06.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100404)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560319] pcieport-driver 0000:00:07.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560327] pcieport-driver 0000:00:07.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560332] pcieport-driver 0000:00:07.0: restoring config space at offset 0x8 (was 0x0, writing 0xf030f030)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560336] pcieport-driver 0000:00:07.0: restoring config space at offset 0x7 (was 0x101, writing 0x200001f1)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560341] pcieport-driver 0000:00:07.0: restoring config space at offset 0x6 (was 0x0, writing 0xa0800)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560347] pcieport-driver 0000:00:07.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560353] pcieport-driver 0000:00:07.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560407] ahci 0000:00:12.0: restoring config space at offset 0x2 (was 0x1018f00, writing 0x1060100)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560431] ahci 0000:00:12.0: set SATA to AHCI mode
Nov 23 10:36:43 ubuntu kernel: [ 3475.560462] ohci_hcd 0000:00:13.0: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560499] ohci_hcd 0000:00:13.1: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560535] ohci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560570] ohci_hcd 0000:00:13.3: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560606] ohci_hcd 0000:00:13.4: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560652] ehci_hcd 0000:00:13.5: restoring config space at offset 0x1 (was 0x2b00017, writing 0x2b00013)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560672] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3475.560729] pata_atiixp 0000:00:14.1: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560751] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560779] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560871] pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560898] HDA Intel 0000:01:05.2: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560931] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560950] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xa001)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560957] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0400004)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560963] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Nov 23 10:36:43 ubuntu kernel: [ 3475.560971] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 10:36:43 ubuntu kernel: [ 3475.561029] ath5k 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Nov 23 10:36:43 ubuntu kernel: [ 3475.561050] ath5k 0000:08:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0300004)
Nov 23 10:36:43 ubuntu kernel: [ 3475.561056] ath5k 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Nov 23 10:36:43 ubuntu kernel: [ 3475.561064] ath5k 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Nov 23 10:36:43 ubuntu kernel: [ 3478.992818] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 23 10:36:43 ubuntu kernel: [ 3478.992887] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 10:36:43 ubuntu kernel: [ 3479.020044] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 10:36:43 ubuntu kernel: [ 3479.050040] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 10:36:43 ubuntu kernel: [ 3479.080042] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 10:36:43 ubuntu kernel: [ 3479.110042] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 10:36:43 ubuntu kernel: [ 3479.140041] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3479.140050] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 23 10:36:43 ubuntu kernel: [ 3479.140071] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 10:36:43 ubuntu kernel: [ 3479.140094] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 10:36:43 ubuntu kernel: [ 3479.140139] pci 0000:01:05.0: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3479.140147] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 23 10:36:43 ubuntu kernel: [ 3479.140159] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 23 10:36:43 ubuntu kernel: [ 3479.140183] sky2 0000:02:00.0: PME# disabled
Nov 23 10:36:43 ubuntu kernel: [ 3479.142591] sky2 eth0: enabling interface
Nov 23 10:36:43 ubuntu kernel: [ 3479.142599] ath5k 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 23 10:36:43 ubuntu kernel: [ 3479.320529] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov 23 10:36:43 ubuntu kernel: [ 3479.320533] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov 23 10:36:43 ubuntu kernel: [ 3479.340060] ata3: SATA link down (SStatus 0 SControl 300)
Nov 23 10:36:43 ubuntu kernel: [ 3479.340089] ata2: SATA link down (SStatus 0 SControl 300)
Nov 23 10:36:43 ubuntu kernel: [ 3479.340117] ata4: SATA link down (SStatus 0 SControl 300)
Nov 23 10:36:43 ubuntu kernel: [ 3479.360499] ata5.00: configured for UDMA/33
Nov 23 10:36:43 ubuntu kernel: [ 3479.520038] ata1: softreset failed (device not ready)
Nov 23 10:36:43 ubuntu kernel: [ 3479.520048] ata1: applying SB600 PMP SRST workaround and retrying
Nov 23 10:36:43 ubuntu kernel: [ 3479.700049] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 10:36:43 ubuntu kernel: [ 3479.700451] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 10:36:43 ubuntu kernel: [ 3479.700965] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 10:36:43 ubuntu kernel: [ 3479.700969] ata1.00: configured for UDMA/100
Nov 23 10:36:43 ubuntu kernel: [ 3479.740048] usb 1-9: reset high speed USB device using ehci_hcd and address 3
Nov 23 10:36:43 ubuntu bluetoothd[905]: HCI dev 0 up
Nov 23 10:36:43 ubuntu bluetoothd[905]: Starting security manager 0
Nov 23 10:36:43 ubuntu kernel: [ 3479.976973] sd 0:0:0:0: [sda] Starting disk
Nov 23 10:36:43 ubuntu kernel: [ 3480.140040] usb 5-2: reset full speed USB device using ohci_hcd and address 2
Nov 23 10:36:43 ubuntu kernel: [ 3480.396082] btusb 5-2:1.0: no reset_resume for driver btusb?
Nov 23 10:36:43 ubuntu kernel: [ 3480.396087] btusb 5-2:1.1: no reset_resume for driver btusb?
Nov 23 10:36:43 ubuntu kernel: [ 3480.640448] PM: resume devices took 5.080 seconds
Nov 23 10:36:43 ubuntu kernel: [ 3480.640450] ------------[ cut here ]------------
Nov 23 10:36:43 ubuntu kernel: [ 3480.640459] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:52 suspend_test_finish+0x7c/0x80()
Nov 23 10:36:43 ubuntu kernel: [ 3480.640462] Hardware name: E300-A.CPB1A9
Nov 23 10:36:43 ubuntu kernel: [ 3480.640463] Component: resume devices
Nov 23 10:36:43 ubuntu kernel: [ 3480.640465] Modules linked in: hidp cryptd aes_x86_64 aes_generic bridge stp bnep snd_hda_codec_atihdmi arc4 joydev ecb snd_hda_codec_realtek snd_hda_intel iptable_filter ath5k snd_hda_codec ip_tables radeon mac80211 snd_hwdep uvcvideo ttm led_class x_tables videodev snd_pcm ath drm v4l1_compat snd_timer snd soundcore i2c_algo_bit v4l2_compat_ioctl32 psmouse snd_page_alloc shpchp lp i2c_piix4 video serio_raw btusb cfg80211 output parport sky2
Nov 23 10:36:43 ubuntu kernel: [ 3480.640502] Pid: 1556, comm: pm-suspend Not tainted 2.6.31-14-generic #48-Ubuntu
Nov 23 10:36:43 ubuntu kernel: [ 3480.640505] Call Trace:
Nov 23 10:36:43 ubuntu kernel: [ 3480.640513]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
Nov 23 10:36:43 ubuntu kernel: [ 3480.640517]  [<ffffffff8105e81c>] warn_slowpath_fmt+0x3c/0x40
Nov 23 10:36:43 ubuntu kernel: [ 3480.640521]  [<ffffffff810934dc>] suspend_test_finish+0x7c/0x80
Nov 23 10:36:43 ubuntu kernel: [ 3480.640525]  [<ffffffff81093289>] suspend_devices_and_enter+0xa9/0xe0
Nov 23 10:36:43 ubuntu kernel: [ 3480.640529]  [<ffffffff81093398>] enter_state+0xd8/0x110
Nov 23 10:36:43 ubuntu kernel: [ 3480.640532]  [<ffffffff81092952>] state_store+0x92/0x100
Nov 23 10:36:43 ubuntu kernel: [ 3480.640538]  [<ffffffff81274197>] kobj_attr_store+0x17/0x20
Nov 23 10:36:43 ubuntu kernel: [ 3480.640544]  [<ffffffff81184780>] sysfs_write_file+0xe0/0x160
Nov 23 10:36:43 ubuntu kernel: [ 3480.640549]  [<ffffffff8111ede8>] vfs_write+0xb8/0x1a0
Nov 23 10:36:43 ubuntu kernel: [ 3480.640554]  [<ffffffff8152bf74>] ? do_page_fault+0x194/0x370
Nov 23 10:36:43 ubuntu kernel: [ 3480.640558]  [<ffffffff8111f89c>] sys_write+0x4c/0x80
Nov 23 10:36:43 ubuntu kernel: [ 3480.640563]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Nov 23 10:36:43 ubuntu kernel: [ 3480.640566] ---[ end trace c697a13ab15cadc3 ]---
Nov 23 10:36:43 ubuntu kernel: [ 3480.640737] PM: Finishing wakeup.
Nov 23 10:36:43 ubuntu kernel: [ 3480.640739] Restarting tasks ... done.
Nov 23 10:36:44 ubuntu bluetoothd[905]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Nov 23 10:36:44 ubuntu bluetoothd[905]: Adapter /org/bluez/895/hci0 has been enabled
Nov 23 10:36:44 ubuntu bluetoothd[905]: return_link_keys (sba=00:0D:F0:48:EB:7D, dba=00:04:61:80:DB:D9)
Nov 23 10:36:44 ubuntu NetworkManager: <info>  Waking up...
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): now managed
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov 23 10:36:44 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:44 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:44 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:44 ubuntu kernel: [ 3481.370532] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov 23 10:36:44 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Nov 23 10:36:44 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:44 ubuntu wpa_supplicant[1069]: Failed to initiate AP scan.
Nov 23 10:36:45 ubuntu kernel: [ 3482.229695] [drm] Loading RS600 Microcode
Nov 23 10:36:45 ubuntu kernel: [ 3482.229723] [drm] Num pipes: 1
Nov 23 10:36:49 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:36:49 ubuntu wpa_supplicant[1069]: WPS-AP-AVAILABLE 
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Wireless'
Nov 23 10:36:49 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 23 10:36:49 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Wireless' has security, and secrets exist.  No new secrets needed.
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'APR1'
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov 23 10:36:49 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 10:36:49 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 23 10:36:49 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 23 10:36:49 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 23 10:36:54 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: WPS-AP-AVAILABLE 
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: Trying to associate with 00:1d:7e:be:a2:cb (SSID='APR1' freq=2437 MHz)
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: Association request to the driver failed
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: Associated with 00:1d:7e:be:a2:cb
Nov 23 10:36:56 ubuntu kernel: [ 3493.142594] wlan0: authenticate with AP 00:1d:7e:be:a2:cb
Nov 23 10:36:56 ubuntu kernel: [ 3493.144032] wlan0: authenticated
Nov 23 10:36:56 ubuntu kernel: [ 3493.144036] wlan0: associate with AP 00:1d:7e:be:a2:cb
Nov 23 10:36:56 ubuntu kernel: [ 3493.146300] wlan0: RX AssocResp from 00:1d:7e:be:a2:cb (capab=0x411 status=0 aid=1)
Nov 23 10:36:56 ubuntu kernel: [ 3493.146303] wlan0: associated
Nov 23 10:36:56 ubuntu kernel: [ 3493.146938] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: WPA: Key negotiation completed with 00:1d:7e:be:a2:cb [PTK=CCMP GTK=CCMP]
Nov 23 10:36:56 ubuntu wpa_supplicant[1069]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:be:a2:cb completed (auth) [id=0 id_str=]
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'APR1'.
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 23 10:36:56 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 23 10:36:56 ubuntu NetworkManager: <info>  dhclient started with pid 1779
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 23 10:36:56 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 23 10:36:56 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov 23 10:36:56 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 23 10:36:56 ubuntu dhclient: All rights reserved.
Nov 23 10:36:56 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 23 10:36:56 ubuntu dhclient: 
Nov 23 10:36:56 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Nov 23 10:36:56 ubuntu dhclient: Listening on LPF/wlan0/00:15:af:52:c1:c8
Nov 23 10:36:56 ubuntu dhclient: Sending on   LPF/wlan0/00:15:af:52:c1:c8
Nov 23 10:36:56 ubuntu dhclient: Sending on   Socket/fallback
Nov 23 10:36:58 ubuntu dhclient: DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
Nov 23 10:36:58 ubuntu dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Nov 23 10:36:58 ubuntu dhclient: bound to 192.168.1.103 -- renewal in 33188 seconds.
Nov 23 10:36:58 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Nov 23 10:36:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 23 10:36:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 23 10:36:58 ubuntu NetworkManager: <info>    address 192.168.1.103
Nov 23 10:36:58 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 23 10:36:58 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Nov 23 10:36:58 ubuntu NetworkManager: <info>    hostname 'ubuntu'
Nov 23 10:36:58 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Nov 23 10:36:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 23 10:36:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 23 10:36:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov 23 10:36:59 ubuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Nov 23 10:36:59 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 10:36:59 ubuntu NetworkManager: <info>  Policy set 'Wireless' (wlan0) as default for routing and DNS.
Nov 23 10:36:59 ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov 23 10:36:59 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 23 10:36:59 ubuntu ntpdate[1796]: adjust time server 91.189.94.4 offset -0.322298 sec
Nov 23 10:37:06 ubuntu kernel: [ 3503.690027] wlan0: no IPv6 routers present
Nov 23 10:37:11 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:37:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:38:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 10:38:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:38:22 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov 23 10:38:42 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 10:38:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:38:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 10:39:09 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:39:09 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:40:11 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:40:14 ubuntu kernel: [ 3690.767309] CE: hpet increasing min_delta_ns to 15000 nsec
Nov 23 10:41:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:42:39 ubuntu kernel: [ 3835.957676] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:42/input11
Nov 23 10:42:39 ubuntu kernel: [ 3835.957837] generic-bluetooth 0005:046D:B003.0002: input,hidraw1: BLUETOOTH HID v43.20 Mouse [Logitech MX1000 mouse] on 00:0D:F0:48:EB:7D
Nov 23 10:43:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:45:22 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 10:45:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 10:45:43 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 10:45:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:46:00 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 10:46:10 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 10:46:23 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:46:23 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:47:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:49:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:51:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:52:27 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 10:52:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 10:52:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 10:52:49 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 10:52:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 10:53:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 10:53:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 10:53:28 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 10:53:28 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 10:53:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:55:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:56:57 ubuntu kernel: [ 4694.007852] CPU0: Temperature above threshold, cpu clock throttled (total events = 1)
Nov 23 10:56:57 ubuntu kernel: [ 4694.007861] Disabling lock debugging due to kernel taint
Nov 23 10:56:57 ubuntu kernel: [ 4694.008633] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.051955] CPU0: Temperature above threshold, cpu clock throttled (total events = 2)
Nov 23 10:56:57 ubuntu kernel: [ 4694.052739] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.188814] CPU0: Temperature above threshold, cpu clock throttled (total events = 3)
Nov 23 10:56:57 ubuntu kernel: [ 4694.189597] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.199718] CPU0: Temperature above threshold, cpu clock throttled (total events = 4)
Nov 23 10:56:57 ubuntu kernel: [ 4694.200519] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.264500] CPU0: Temperature above threshold, cpu clock throttled (total events = 5)
Nov 23 10:56:57 ubuntu kernel: [ 4694.265285] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.318344] CPU0: Temperature above threshold, cpu clock throttled (total events = 6)
Nov 23 10:56:57 ubuntu kernel: [ 4694.319128] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.346303] CPU0: Temperature above threshold, cpu clock throttled (total events = 7)
Nov 23 10:56:57 ubuntu kernel: [ 4694.347088] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.477826] CPU0: Temperature above threshold, cpu clock throttled (total events = 8)
Nov 23 10:56:57 ubuntu kernel: [ 4694.478609] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.555718] CPU0: Temperature above threshold, cpu clock throttled (total events = 9)
Nov 23 10:56:57 ubuntu kernel: [ 4694.556502] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.606329] CPU0: Temperature above threshold, cpu clock throttled (total events = 10)
Nov 23 10:56:57 ubuntu kernel: [ 4694.607114] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.654863] CPU0: Temperature above threshold, cpu clock throttled (total events = 11)
Nov 23 10:56:57 ubuntu kernel: [ 4694.655647] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.709072] CPU0: Temperature above threshold, cpu clock throttled (total events = 12)
Nov 23 10:56:57 ubuntu kernel: [ 4694.709855] CPU0: Temperature/speed normal
Nov 23 10:56:57 ubuntu kernel: [ 4694.739898] CPU0: Temperature above threshold, cpu clock throttled (total events = 13)
Nov 23 10:56:57 ubuntu kernel: [ 4694.740698] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4694.826966] CPU0: Temperature above threshold, cpu clock throttled (total events = 14)
Nov 23 10:56:58 ubuntu kernel: [ 4694.827749] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.020333] CPU0: Temperature above threshold, cpu clock throttled (total events = 15)
Nov 23 10:56:58 ubuntu kernel: [ 4695.021115] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.087995] CPU0: Temperature above threshold, cpu clock throttled (total events = 16)
Nov 23 10:56:58 ubuntu kernel: [ 4695.088779] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.205795] CPU0: Temperature above threshold, cpu clock throttled (total events = 17)
Nov 23 10:56:58 ubuntu kernel: [ 4695.206579] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.235217] CPU0: Temperature above threshold, cpu clock throttled (total events = 18)
Nov 23 10:56:58 ubuntu kernel: [ 4695.236002] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.265352] CPU0: Temperature above threshold, cpu clock throttled (total events = 19)
Nov 23 10:56:58 ubuntu kernel: [ 4695.266137] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.309845] CPU0: Temperature above threshold, cpu clock throttled (total events = 20)
Nov 23 10:56:58 ubuntu kernel: [ 4695.310645] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.329427] CPU0: Temperature above threshold, cpu clock throttled (total events = 21)
Nov 23 10:56:58 ubuntu kernel: [ 4695.330228] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.379029] CPU0: Temperature above threshold, cpu clock throttled (total events = 22)
Nov 23 10:56:58 ubuntu kernel: [ 4695.379814] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.416060] CPU0: Temperature above threshold, cpu clock throttled (total events = 23)
Nov 23 10:56:58 ubuntu kernel: [ 4695.416846] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.483440] CPU0: Temperature above threshold, cpu clock throttled (total events = 24)
Nov 23 10:56:58 ubuntu kernel: [ 4695.484224] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.516482] CPU0: Temperature above threshold, cpu clock throttled (total events = 25)
Nov 23 10:56:58 ubuntu kernel: [ 4695.517267] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.547317] CPU0: Temperature above threshold, cpu clock throttled (total events = 26)
Nov 23 10:56:58 ubuntu kernel: [ 4695.548101] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.583810] CPU0: Temperature above threshold, cpu clock throttled (total events = 27)
Nov 23 10:56:58 ubuntu kernel: [ 4695.584594] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.635251] CPU0: Temperature above threshold, cpu clock throttled (total events = 28)
Nov 23 10:56:58 ubuntu kernel: [ 4695.636035] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.685825] CPU0: Temperature above threshold, cpu clock throttled (total events = 29)
Nov 23 10:56:58 ubuntu kernel: [ 4695.686608] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.710770] CPU0: Temperature above threshold, cpu clock throttled (total events = 30)
Nov 23 10:56:58 ubuntu kernel: [ 4695.711555] CPU0: Temperature/speed normal
Nov 23 10:56:58 ubuntu kernel: [ 4695.741753] CPU0: Temperature above threshold, cpu clock throttled (total events = 31)
Nov 23 10:56:58 ubuntu kernel: [ 4695.742538] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.770303] CPU0: Temperature above threshold, cpu clock throttled (total events = 32)
Nov 23 10:56:59 ubuntu kernel: [ 4695.771088] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.798105] CPU0: Temperature above threshold, cpu clock throttled (total events = 33)
Nov 23 10:56:59 ubuntu kernel: [ 4695.798890] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.821978] CPU0: Temperature above threshold, cpu clock throttled (total events = 34)
Nov 23 10:56:59 ubuntu kernel: [ 4695.822763] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.846816] CPU0: Temperature above threshold, cpu clock throttled (total events = 35)
Nov 23 10:56:59 ubuntu kernel: [ 4695.847601] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.882312] CPU0: Temperature above threshold, cpu clock throttled (total events = 36)
Nov 23 10:56:59 ubuntu kernel: [ 4695.883098] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.908663] CPU0: Temperature above threshold, cpu clock throttled (total events = 37)
Nov 23 10:56:59 ubuntu kernel: [ 4695.909449] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.965479] CPU0: Temperature above threshold, cpu clock throttled (total events = 38)
Nov 23 10:56:59 ubuntu kernel: [ 4695.966264] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4695.987590] CPU0: Temperature above threshold, cpu clock throttled (total events = 39)
Nov 23 10:56:59 ubuntu kernel: [ 4695.988376] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.016382] CPU0: Temperature above threshold, cpu clock throttled (total events = 40)
Nov 23 10:56:59 ubuntu kernel: [ 4696.017168] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.045424] CPU0: Temperature above threshold, cpu clock throttled (total events = 41)
Nov 23 10:56:59 ubuntu kernel: [ 4696.046209] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.058578] CPU0: Temperature above threshold, cpu clock throttled (total events = 42)
Nov 23 10:56:59 ubuntu kernel: [ 4696.059364] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.088156] CPU0: Temperature above threshold, cpu clock throttled (total events = 43)
Nov 23 10:56:59 ubuntu kernel: [ 4696.088941] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.113194] CPU0: Temperature above threshold, cpu clock throttled (total events = 44)
Nov 23 10:56:59 ubuntu kernel: [ 4696.113979] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.135880] CPU0: Temperature above threshold, cpu clock throttled (total events = 45)
Nov 23 10:56:59 ubuntu kernel: [ 4696.136665] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.156782] CPU0: Temperature above threshold, cpu clock throttled (total events = 46)
Nov 23 10:56:59 ubuntu kernel: [ 4696.157568] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.230130] CPU0: Temperature above threshold, cpu clock throttled (total events = 47)
Nov 23 10:56:59 ubuntu kernel: [ 4696.230914] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.273410] CPU0: Temperature above threshold, cpu clock throttled (total events = 48)
Nov 23 10:56:59 ubuntu kernel: [ 4696.274195] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.283754] CPU0: Temperature above threshold, cpu clock throttled (total events = 49)
Nov 23 10:56:59 ubuntu kernel: [ 4696.284540] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.326576] CPU0: Temperature above threshold, cpu clock throttled (total events = 50)
Nov 23 10:56:59 ubuntu kernel: [ 4696.327362] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.360258] CPU0: Temperature above threshold, cpu clock throttled (total events = 51)
Nov 23 10:56:59 ubuntu kernel: [ 4696.361043] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.381328] CPU0: Temperature above threshold, cpu clock throttled (total events = 52)
Nov 23 10:56:59 ubuntu kernel: [ 4696.382113] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.408754] CPU0: Temperature above threshold, cpu clock throttled (total events = 53)
Nov 23 10:56:59 ubuntu kernel: [ 4696.409540] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.417348] CPU0: Temperature above threshold, cpu clock throttled (total events = 54)
Nov 23 10:56:59 ubuntu kernel: [ 4696.418134] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.446820] CPU0: Temperature above threshold, cpu clock throttled (total events = 55)
Nov 23 10:56:59 ubuntu kernel: [ 4696.447605] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.467401] CPU0: Temperature above threshold, cpu clock throttled (total events = 56)
Nov 23 10:56:59 ubuntu kernel: [ 4696.468187] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.502432] CPU0: Temperature above threshold, cpu clock throttled (total events = 57)
Nov 23 10:56:59 ubuntu kernel: [ 4696.503217] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.529392] CPU0: Temperature above threshold, cpu clock throttled (total events = 58)
Nov 23 10:56:59 ubuntu kernel: [ 4696.530193] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.553204] CPU0: Temperature above threshold, cpu clock throttled (total events = 59)
Nov 23 10:56:59 ubuntu kernel: [ 4696.553990] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.585865] CPU0: Temperature above threshold, cpu clock throttled (total events = 60)
Nov 23 10:56:59 ubuntu kernel: [ 4696.586650] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.600617] CPU0: Temperature above threshold, cpu clock throttled (total events = 61)
Nov 23 10:56:59 ubuntu kernel: [ 4696.601402] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.626789] CPU0: Temperature above threshold, cpu clock throttled (total events = 62)
Nov 23 10:56:59 ubuntu kernel: [ 4696.627574] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.634945] CPU0: Temperature above threshold, cpu clock throttled (total events = 63)
Nov 23 10:56:59 ubuntu kernel: [ 4696.635731] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.646583] CPU0: Temperature above threshold, cpu clock throttled (total events = 64)
Nov 23 10:56:59 ubuntu kernel: [ 4696.647368] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.679275] CPU0: Temperature above threshold, cpu clock throttled (total events = 65)
Nov 23 10:56:59 ubuntu kernel: [ 4696.680075] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.705647] CPU0: Temperature above threshold, cpu clock throttled (total events = 66)
Nov 23 10:56:59 ubuntu kernel: [ 4696.706432] CPU0: Temperature/speed normal
Nov 23 10:56:59 ubuntu kernel: [ 4696.725459] CPU0: Temperature above threshold, cpu clock throttled (total events = 67)
Nov 23 10:56:59 ubuntu kernel: [ 4696.726244] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.750506] CPU0: Temperature above threshold, cpu clock throttled (total events = 68)
Nov 23 10:57:00 ubuntu kernel: [ 4696.751291] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.762343] CPU0: Temperature above threshold, cpu clock throttled (total events = 69)
Nov 23 10:57:00 ubuntu kernel: [ 4696.763128] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.826695] CPU0: Temperature above threshold, cpu clock throttled (total events = 70)
Nov 23 10:57:00 ubuntu kernel: [ 4696.827480] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.862530] CPU0: Temperature above threshold, cpu clock throttled (total events = 71)
Nov 23 10:57:00 ubuntu kernel: [ 4696.863315] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.886939] CPU0: Temperature above threshold, cpu clock throttled (total events = 72)
Nov 23 10:57:00 ubuntu kernel: [ 4696.887725] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.894247] CPU0: Temperature above threshold, cpu clock throttled (total events = 73)
Nov 23 10:57:00 ubuntu kernel: [ 4696.895032] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.914839] CPU0: Temperature above threshold, cpu clock throttled (total events = 74)
Nov 23 10:57:00 ubuntu kernel: [ 4696.915624] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.952726] CPU0: Temperature above threshold, cpu clock throttled (total events = 75)
Nov 23 10:57:00 ubuntu kernel: [ 4696.953510] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.960968] CPU0: Temperature above threshold, cpu clock throttled (total events = 76)
Nov 23 10:57:00 ubuntu kernel: [ 4696.961754] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4696.986657] CPU0: Temperature above threshold, cpu clock throttled (total events = 77)
Nov 23 10:57:00 ubuntu kernel: [ 4696.987442] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.004875] CPU0: Temperature above threshold, cpu clock throttled (total events = 78)
Nov 23 10:57:00 ubuntu kernel: [ 4697.005660] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.016315] CPU0: Temperature above threshold, cpu clock throttled (total events = 79)
Nov 23 10:57:00 ubuntu kernel: [ 4697.017100] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.041169] CPU0: Temperature above threshold, cpu clock throttled (total events = 80)
Nov 23 10:57:00 ubuntu kernel: [ 4697.041954] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.053003] CPU0: Temperature above threshold, cpu clock throttled (total events = 81)
Nov 23 10:57:00 ubuntu kernel: [ 4697.053789] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.066804] CPU0: Temperature above threshold, cpu clock throttled (total events = 82)
Nov 23 10:57:00 ubuntu kernel: [ 4697.067590] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.085844] CPU0: Temperature above threshold, cpu clock throttled (total events = 83)
Nov 23 10:57:00 ubuntu kernel: [ 4697.086630] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.115316] CPU0: Temperature above threshold, cpu clock throttled (total events = 84)
Nov 23 10:57:00 ubuntu kernel: [ 4697.116101] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.139452] CPU0: Temperature above threshold, cpu clock throttled (total events = 85)
Nov 23 10:57:00 ubuntu kernel: [ 4697.140253] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.157317] CPU0: Temperature above threshold, cpu clock throttled (total events = 86)
Nov 23 10:57:00 ubuntu kernel: [ 4697.158103] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.171981] CPU0: Temperature above threshold, cpu clock throttled (total events = 87)
Nov 23 10:57:00 ubuntu kernel: [ 4697.172766] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.182960] CPU0: Temperature above threshold, cpu clock throttled (total events = 88)
Nov 23 10:57:00 ubuntu kernel: [ 4697.183746] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.194015] CPU0: Temperature above threshold, cpu clock throttled (total events = 89)
Nov 23 10:57:00 ubuntu kernel: [ 4697.194801] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.208211] CPU0: Temperature above threshold, cpu clock throttled (total events = 90)
Nov 23 10:57:00 ubuntu kernel: [ 4697.208996] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.228067] CPU0: Temperature above threshold, cpu clock throttled (total events = 91)
Nov 23 10:57:00 ubuntu kernel: [ 4697.228853] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.239059] CPU0: Temperature above threshold, cpu clock throttled (total events = 92)
Nov 23 10:57:00 ubuntu kernel: [ 4697.239845] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.255253] CPU0: Temperature above threshold, cpu clock throttled (total events = 93)
Nov 23 10:57:00 ubuntu kernel: [ 4697.256038] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.276154] CPU0: Temperature above threshold, cpu clock throttled (total events = 94)
Nov 23 10:57:00 ubuntu kernel: [ 4697.276940] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.296866] CPU0: Temperature above threshold, cpu clock throttled (total events = 95)
Nov 23 10:57:00 ubuntu kernel: [ 4697.297652] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.311174] CPU0: Temperature above threshold, cpu clock throttled (total events = 96)
Nov 23 10:57:00 ubuntu kernel: [ 4697.311959] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.324819] CPU0: Temperature above threshold, cpu clock throttled (total events = 97)
Nov 23 10:57:00 ubuntu kernel: [ 4697.325604] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.337597] CPU0: Temperature above threshold, cpu clock throttled (total events = 98)
Nov 23 10:57:00 ubuntu kernel: [ 4697.338383] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.366899] CPU0: Temperature above threshold, cpu clock throttled (total events = 99)
Nov 23 10:57:00 ubuntu kernel: [ 4697.367684] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.378615] CPU0: Temperature above threshold, cpu clock throttled (total events = 100)
Nov 23 10:57:00 ubuntu kernel: [ 4697.379400] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.389945] CPU0: Temperature above threshold, cpu clock throttled (total events = 101)
Nov 23 10:57:00 ubuntu kernel: [ 4697.390746] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.411195] CPU0: Temperature above threshold, cpu clock throttled (total events = 102)
Nov 23 10:57:00 ubuntu kernel: [ 4697.411980] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.424184] CPU0: Temperature above threshold, cpu clock throttled (total events = 103)
Nov 23 10:57:00 ubuntu kernel: [ 4697.424970] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.442332] CPU0: Temperature above threshold, cpu clock throttled (total events = 104)
Nov 23 10:57:00 ubuntu kernel: [ 4697.443114] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.459678] CPU0: Temperature above threshold, cpu clock throttled (total events = 105)
Nov 23 10:57:00 ubuntu kernel: [ 4697.460477] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.487589] CPU0: Temperature above threshold, cpu clock throttled (total events = 106)
Nov 23 10:57:00 ubuntu kernel: [ 4697.488375] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.515485] CPU0: Temperature above threshold, cpu clock throttled (total events = 107)
Nov 23 10:57:00 ubuntu kernel: [ 4697.516270] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.535959] CPU0: Temperature above threshold, cpu clock throttled (total events = 108)
Nov 23 10:57:00 ubuntu kernel: [ 4697.536744] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.542935] CPU0: Temperature above threshold, cpu clock throttled (total events = 109)
Nov 23 10:57:00 ubuntu kernel: [ 4697.543721] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.547837] CPU0: Temperature above threshold, cpu clock throttled (total events = 110)
Nov 23 10:57:00 ubuntu kernel: [ 4697.548623] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.570881] CPU0: Temperature above threshold, cpu clock throttled (total events = 111)
Nov 23 10:57:00 ubuntu kernel: [ 4697.571667] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.581573] CPU0: Temperature above threshold, cpu clock throttled (total events = 112)
Nov 23 10:57:00 ubuntu kernel: [ 4697.582359] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.590452] CPU0: Temperature above threshold, cpu clock throttled (total events = 113)
Nov 23 10:57:00 ubuntu kernel: [ 4697.591238] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.606225] CPU0: Temperature above threshold, cpu clock throttled (total events = 114)
Nov 23 10:57:00 ubuntu kernel: [ 4697.607011] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.619556] CPU0: Temperature above threshold, cpu clock throttled (total events = 115)
Nov 23 10:57:00 ubuntu kernel: [ 4697.620357] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.625523] CPU0: Temperature above threshold, cpu clock throttled (total events = 116)
Nov 23 10:57:00 ubuntu kernel: [ 4697.626308] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.651296] CPU0: Temperature above threshold, cpu clock throttled (total events = 117)
Nov 23 10:57:00 ubuntu kernel: [ 4697.652082] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.668360] CPU0: Temperature above threshold, cpu clock throttled (total events = 118)
Nov 23 10:57:00 ubuntu kernel: [ 4697.669145] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.688442] CPU0: Temperature above threshold, cpu clock throttled (total events = 119)
Nov 23 10:57:00 ubuntu kernel: [ 4697.689226] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.708514] CPU0: Temperature above threshold, cpu clock throttled (total events = 120)
Nov 23 10:57:00 ubuntu kernel: [ 4697.709299] CPU0: Temperature/speed normal
Nov 23 10:57:00 ubuntu kernel: [ 4697.738948] CPU0: Temperature above threshold, cpu clock throttled (total events = 121)
Nov 23 10:57:00 ubuntu kernel: [ 4697.739733] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.756020] CPU0: Temperature above threshold, cpu clock throttled (total events = 122)
Nov 23 10:57:01 ubuntu kernel: [ 4697.756806] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.764792] CPU0: Temperature above threshold, cpu clock throttled (total events = 123)
Nov 23 10:57:01 ubuntu kernel: [ 4697.765578] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.790173] CPU0: Temperature above threshold, cpu clock throttled (total events = 124)
Nov 23 10:57:01 ubuntu kernel: [ 4697.790959] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.826312] CPU0: Temperature above threshold, cpu clock throttled (total events = 125)
Nov 23 10:57:01 ubuntu kernel: [ 4697.827096] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.873629] CPU0: Temperature above threshold, cpu clock throttled (total events = 126)
Nov 23 10:57:01 ubuntu kernel: [ 4697.874413] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.882151] CPU0: Temperature above threshold, cpu clock throttled (total events = 127)
Nov 23 10:57:01 ubuntu kernel: [ 4697.882937] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.899661] CPU0: Temperature above threshold, cpu clock throttled (total events = 128)
Nov 23 10:57:01 ubuntu kernel: [ 4697.900462] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.913233] CPU0: Temperature above threshold, cpu clock throttled (total events = 129)
Nov 23 10:57:01 ubuntu kernel: [ 4697.914019] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.936309] CPU0: Temperature above threshold, cpu clock throttled (total events = 130)
Nov 23 10:57:01 ubuntu kernel: [ 4697.937094] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.957448] CPU0: Temperature above threshold, cpu clock throttled (total events = 131)
Nov 23 10:57:01 ubuntu kernel: [ 4697.958233] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.984467] CPU0: Temperature above threshold, cpu clock throttled (total events = 132)
Nov 23 10:57:01 ubuntu kernel: [ 4697.985252] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.987561] CPU0: Temperature above threshold, cpu clock throttled (total events = 133)
Nov 23 10:57:01 ubuntu kernel: [ 4697.988347] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4697.995520] CPU0: Temperature above threshold, cpu clock throttled (total events = 134)
Nov 23 10:57:01 ubuntu kernel: [ 4697.996306] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.019292] CPU0: Temperature above threshold, cpu clock throttled (total events = 135)
Nov 23 10:57:01 ubuntu kernel: [ 4698.020093] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.032998] CPU0: Temperature above threshold, cpu clock throttled (total events = 136)
Nov 23 10:57:01 ubuntu kernel: [ 4698.033784] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.068430] CPU0: Temperature above threshold, cpu clock throttled (total events = 137)
Nov 23 10:57:01 ubuntu kernel: [ 4698.069215] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.082382] CPU0: Temperature above threshold, cpu clock throttled (total events = 138)
Nov 23 10:57:01 ubuntu kernel: [ 4698.083168] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.089081] CPU0: Temperature above threshold, cpu clock throttled (total events = 139)
Nov 23 10:57:01 ubuntu kernel: [ 4698.089867] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.097985] CPU0: Temperature above threshold, cpu clock throttled (total events = 140)
Nov 23 10:57:01 ubuntu kernel: [ 4698.098771] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.112638] CPU0: Temperature above threshold, cpu clock throttled (total events = 141)
Nov 23 10:57:01 ubuntu kernel: [ 4698.113424] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.125749] CPU0: Temperature above threshold, cpu clock throttled (total events = 142)
Nov 23 10:57:01 ubuntu kernel: [ 4698.126535] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.130440] CPU0: Temperature above threshold, cpu clock throttled (total events = 143)
Nov 23 10:57:01 ubuntu kernel: [ 4698.131226] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.153513] CPU0: Temperature above threshold, cpu clock throttled (total events = 144)
Nov 23 10:57:01 ubuntu kernel: [ 4698.154298] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.159230] CPU0: Temperature above threshold, cpu clock throttled (total events = 145)
Nov 23 10:57:01 ubuntu kernel: [ 4698.160033] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.173719] CPU0: Temperature above threshold, cpu clock throttled (total events = 146)
Nov 23 10:57:01 ubuntu kernel: [ 4698.174504] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.195058] CPU0: Temperature above threshold, cpu clock throttled (total events = 147)
Nov 23 10:57:01 ubuntu kernel: [ 4698.195844] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.200224] CPU0: Temperature above threshold, cpu clock throttled (total events = 148)
Nov 23 10:57:01 ubuntu kernel: [ 4698.201009] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.207445] CPU0: Temperature above threshold, cpu clock throttled (total events = 149)
Nov 23 10:57:01 ubuntu kernel: [ 4698.208231] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.221186] CPU0: Temperature above threshold, cpu clock throttled (total events = 150)
Nov 23 10:57:01 ubuntu kernel: [ 4698.221972] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.237916] CPU0: Temperature above threshold, cpu clock throttled (total events = 151)
Nov 23 10:57:01 ubuntu kernel: [ 4698.238701] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.251567] CPU0: Temperature above threshold, cpu clock throttled (total events = 152)
Nov 23 10:57:01 ubuntu kernel: [ 4698.252353] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.264608] CPU0: Temperature above threshold, cpu clock throttled (total events = 153)
Nov 23 10:57:01 ubuntu kernel: [ 4698.265393] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.295925] CPU0: Temperature above threshold, cpu clock throttled (total events = 154)
Nov 23 10:57:01 ubuntu kernel: [ 4698.296710] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.305396] CPU0: Temperature above threshold, cpu clock throttled (total events = 155)
Nov 23 10:57:01 ubuntu kernel: [ 4698.306182] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.327130] CPU0: Temperature above threshold, cpu clock throttled (total events = 156)
Nov 23 10:57:01 ubuntu kernel: [ 4698.327916] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.345875] CPU0: Temperature above threshold, cpu clock throttled (total events = 157)
Nov 23 10:57:01 ubuntu kernel: [ 4698.346661] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.363381] CPU0: Temperature above threshold, cpu clock throttled (total events = 158)
Nov 23 10:57:01 ubuntu kernel: [ 4698.364166] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.382315] CPU0: Temperature above threshold, cpu clock throttled (total events = 159)
Nov 23 10:57:01 ubuntu kernel: [ 4698.383100] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.406945] CPU0: Temperature above threshold, cpu clock throttled (total events = 160)
Nov 23 10:57:01 ubuntu kernel: [ 4698.407730] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.412689] CPU0: Temperature above threshold, cpu clock throttled (total events = 161)
Nov 23 10:57:01 ubuntu kernel: [ 4698.413475] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.438513] CPU0: Temperature above threshold, cpu clock throttled (total events = 162)
Nov 23 10:57:01 ubuntu kernel: [ 4698.439297] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.445369] CPU0: Temperature above threshold, cpu clock throttled (total events = 163)
Nov 23 10:57:01 ubuntu kernel: [ 4698.446155] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.471619] CPU0: Temperature above threshold, cpu clock throttled (total events = 164)
Nov 23 10:57:01 ubuntu kernel: [ 4698.472404] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.491379] CPU0: Temperature above threshold, cpu clock throttled (total events = 165)
Nov 23 10:57:01 ubuntu kernel: [ 4698.492164] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.497489] CPU0: Temperature above threshold, cpu clock throttled (total events = 166)
Nov 23 10:57:01 ubuntu kernel: [ 4698.498276] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.508536] CPU0: Temperature above threshold, cpu clock throttled (total events = 167)
Nov 23 10:57:01 ubuntu kernel: [ 4698.509322] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.529111] CPU0: Temperature above threshold, cpu clock throttled (total events = 168)
Nov 23 10:57:01 ubuntu kernel: [ 4698.529897] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.534778] CPU0: Temperature above threshold, cpu clock throttled (total events = 169)
Nov 23 10:57:01 ubuntu kernel: [ 4698.535564] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.554322] CPU0: Temperature above threshold, cpu clock throttled (total events = 170)
Nov 23 10:57:01 ubuntu kernel: [ 4698.555107] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.579796] CPU0: Temperature above threshold, cpu clock throttled (total events = 171)
Nov 23 10:57:01 ubuntu kernel: [ 4698.580597] CPU0: Temperature/speed normal
Nov 23 10:57:01 ubuntu kernel: [ 4698.587354] CPU0: Temperature above threshold, cpu clock throttled (total events = 172)
Nov 23 10:57:01 ubuntu kernel: [ 4698.588140] CPU0: Temperature/speed normal
Nov 23 10:57:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 10:58:43 ubuntu kernel: [ 4800.040035] Machine check events logged
Nov 23 10:59:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:00:04 ubuntu wpa_supplicant[1069]: WPA: Group rekeying completed with 00:1d:7e:be:a2:cb [GTK=CCMP]
Nov 23 11:00:04 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov 23 11:00:04 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 11:00:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:00:18 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 11:00:29 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:00:43 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Nov 23 11:01:01 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 11:01:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov 23 11:01:13 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:01:13 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:01:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:03:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:05:51 ubuntu wpa_supplicant[1069]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:05:53 ubuntu kernel: [ 5230.715096] arora[1369]: segfault at 10 ip 00007f5d881b2677 sp 00007fff1cc24cb0 error 4 in libplds4.so[7f5d881b1000+3000]
Nov 23 11:06:10 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 38)
Nov 23 11:06:10 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 38).
Nov 23 11:06:10 ubuntu NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1779
Nov 23 11:06:10 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov 23 11:06:10 ubuntu kernel: [ 5247.616712] wlan0: disassociating by local choice (reason=3)
Nov 23 11:06:10 ubuntu wpa_supplicant[1069]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 23 11:06:10 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:11 ubuntu kernel: [ 5248.685303] [drm] Num pipes: 1
Nov 23 11:06:12 ubuntu kernel: [ 5249.136786] mtrr: MTRR 4 not used
Nov 23 11:06:12 ubuntu kernel: Kernel logging (proc) stopped.
Nov 23 11:06:36 ubuntu kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 23 11:06:36 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="750" x-info="http://www.rsyslog.com"] (re)start
Nov 23 11:06:37 ubuntu rsyslogd: rsyslogd's groupid changed to 102
Nov 23 11:06:37 ubuntu rsyslogd: rsyslogd's userid changed to 101
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=d064dc83-f39c-42ed-8e93-7968c59c4149 ro splash quiet
Nov 23 11:06:37 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Nov 23 11:06:37 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe80000 (usable)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000006fe80000 - 000000006fe98000 (ACPI data)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000006fe98000 - 000000006fe9a000 (ACPI NVS)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000006fe9a000 - 0000000070000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] DMI present.
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Nov 23 11:06:37 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] last_pfn = 0x6fe80 max_arch_pfn = 0x400000000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Nov 23 11:06:37 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   D0000-DFFFF uncachable
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   E0000-FFFFF write-protect
Nov 23 11:06:37 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   2 base 060000000 mask FF0000000 write-back
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   3 base 06FF00000 mask FFFF00000 uncachable
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   4 disabled
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   5 disabled
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   6 disabled
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   7 disabled
Nov 23 11:06:37 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Nov 23 11:06:37 ubuntu kernel: [    0.000000] modified physical RAM map:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000000dc000 - 00000000000e0000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000006fe80000 (usable)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 000000006fe80000 - 000000006fe98000 (ACPI data)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 000000006fe98000 - 000000006fe9a000 (ACPI NVS)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 000000006fe9a000 - 0000000070000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000006fe80000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  0000000000 - 006fe00000 page 2M
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  006fe00000 - 006fe80000 page 4k
Nov 23 11:06:37 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 6fe80000 @ 10000-14000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] RAMDISK: 37956000 - 37fef3ef
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7e90 00024 (v02 PTLTD )
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: XSDT 000000006fe89e86 0006C (v01 LGE    LGPC     06040000  LTP 00000000)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: TCPA 000000006fe97c9c 00032 (v02 INTEL           06040000 PTEC 00000000)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: FACP 000000006fe97cce 000F4 (v03 ATI    Alfonsin 06040000 ATI  000F4240)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: DSDT 000000006fe8d774 0A4B4 (v01    LGE  LHOTSE2 06040000 MSFT 0100000E)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: FACS 000000006fe99fc0 00040
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: SLIC 000000006fe97dc2 00176 (v01 LGE    LGPC     06040000 YSB  00000001)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: APIC 000000006fe97f38 00054 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: MCFG 000000006fe97f8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: HPET 000000006fe97fc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: SSDT 000000006fe8b39d 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: SSDT 000000006fe8b2f7 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: SSDT 000000006fe89ef2 01405 (v01  PmRef    CpuPm 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] No NUMA configuration found
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000006fe80000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000006fe80000
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000024fcf] pages e
Nov 23 11:06:37 ubuntu kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 006fe80000]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #3 [0037956000 - 0037fef3ef]          RAMDISK ==> [0037956000 - 0037fef3ef]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #5 [00019e3000 - 00019e3164]              BRK ==> [00019e3000 - 00019e3164]
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Nov 23 11:06:37 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f7ec0] f7ec0
Nov 23 11:06:37 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880001e00000-ffff8800037fffff] on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Zone PFN ranges:
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Nov 23 11:06:37 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov 23 11:06:37 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Nov 23 11:06:37 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0006fe80
Nov 23 11:06:37 ubuntu kernel: [    0.000000] On node 0 totalpages: 458253
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA zone: 103 pages reserved
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA zone: 3822 pages, LIFO batch:0
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA32 zone: 6211 pages used for memmap
Nov 23 11:06:37 ubuntu kernel: [    0.000000]   DMA32 zone: 448061 pages, LIFO batch:31
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 23 11:06:37 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 23 11:06:37 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov 23 11:06:37 ubuntu kernel: [    0.000000] nr_irqs_gsi: 24
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 70000000:70000000)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff8800019f4000, static data 90720 bytes
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 451883
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Policy zone: DMA32
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=d064dc83-f39c-42ed-8e93-7968c59c4149 ro splash quiet
Nov 23 11:06:37 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Initializing CPU#0
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Checking aperture...
Nov 23 11:06:37 ubuntu kernel: [    0.000000] No AGP bridge found
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Memory: 1789104k/1833472k available (5313k kernel code, 460k absent, 43908k reserved, 3011k data, 660k init)
Nov 23 11:06:37 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 23 11:06:37 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Nov 23 11:06:37 ubuntu kernel: [    0.000000] Detected 1662.715 MHz processor.
Nov 23 11:06:37 ubuntu kernel: [    0.000675] Console: colour VGA+ 80x25
Nov 23 11:06:37 ubuntu kernel: [    0.000678] console [tty0] enabled
Nov 23 11:06:37 ubuntu kernel: [    0.010000] allocated 18350080 bytes of page_cgroup
Nov 23 11:06:37 ubuntu kernel: [    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 23 11:06:37 ubuntu kernel: [    0.010000] hpet clockevent registered
Nov 23 11:06:37 ubuntu kernel: [    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Nov 23 11:06:37 ubuntu kernel: [    0.010013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.43 BogoMIPS (lpj=16627150)
Nov 23 11:06:37 ubuntu kernel: [    0.010052] Security Framework initialized
Nov 23 11:06:37 ubuntu kernel: [    0.010084] AppArmor: AppArmor initialized
Nov 23 11:06:37 ubuntu kernel: [    0.010338] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.012075] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.013008] Mount-cache hash table entries: 256
Nov 23 11:06:37 ubuntu kernel: [    0.013232] Initializing cgroup subsys ns
Nov 23 11:06:37 ubuntu kernel: [    0.013241] Initializing cgroup subsys cpuacct
Nov 23 11:06:37 ubuntu kernel: [    0.013246] Initializing cgroup subsys memory
Nov 23 11:06:37 ubuntu kernel: [    0.013257] Initializing cgroup subsys freezer
Nov 23 11:06:37 ubuntu kernel: [    0.013260] Initializing cgroup subsys net_cls
Nov 23 11:06:37 ubuntu kernel: [    0.013279] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 11:06:37 ubuntu kernel: [    0.013282] CPU: L2 cache: 2048K
Nov 23 11:06:37 ubuntu kernel: [    0.013287] CPU 0/0x0 -> Node 0
Nov 23 11:06:37 ubuntu kernel: [    0.013290] CPU: Physical Processor ID: 0
Nov 23 11:06:37 ubuntu kernel: [    0.013292] CPU: Processor Core ID: 0
Nov 23 11:06:37 ubuntu kernel: [    0.013296] mce: CPU supports 6 MCE banks
Nov 23 11:06:37 ubuntu kernel: [    0.013306] CPU0: Thermal monitoring enabled (TM2)
Nov 23 11:06:37 ubuntu kernel: [    0.013312] using mwait in idle threads.
Nov 23 11:06:37 ubuntu kernel: [    0.013314] Performance Counters: Core2 events, Intel PMU driver.
Nov 23 11:06:37 ubuntu kernel: [    0.013322] ... version:                 2
Nov 23 11:06:37 ubuntu kernel: [    0.013324] ... bit width:               40
Nov 23 11:06:37 ubuntu kernel: [    0.013325] ... generic counters:        2
Nov 23 11:06:37 ubuntu kernel: [    0.013327] ... value mask:              000000ffffffffff
Nov 23 11:06:37 ubuntu kernel: [    0.013330] ... max period:              000000007fffffff
Nov 23 11:06:37 ubuntu kernel: [    0.013331] ... fixed-purpose counters:  3
Nov 23 11:06:37 ubuntu kernel: [    0.013333] ... counter mask:            0000000700000003
Nov 23 11:06:37 ubuntu kernel: [    0.016570] ACPI: Core revision 20090521
Nov 23 11:06:37 ubuntu kernel: [    0.040076] Setting APIC routing to flat
Nov 23 11:06:37 ubuntu kernel: [    0.040400] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 23 11:06:37 ubuntu kernel: [    0.050000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Nov 23 11:06:37 ubuntu kernel: [    0.050000] ...trying to set up timer (IRQ0) through the 8259A ...
Nov 23 11:06:37 ubuntu kernel: [    0.050000] ..... (found apic 0 pin 0) ...
Nov 23 11:06:37 ubuntu kernel: [    0.152865] ....... works.
Nov 23 11:06:37 ubuntu kernel: [    0.152867] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Nov 23 11:06:37 ubuntu kernel: [    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
Nov 23 11:06:37 ubuntu kernel: [    0.010000] Initializing CPU#1
Nov 23 11:06:37 ubuntu kernel: [    0.010000] Calibrating delay using timer specific routine.. 3325.00 BogoMIPS (lpj=16625046)
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU: L2 cache: 2048K
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU 1/0x1 -> Node 0
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU: Physical Processor ID: 0
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU: Processor Core ID: 1
Nov 23 11:06:37 ubuntu kernel: [    0.010000] mce: CPU supports 6 MCE banks
Nov 23 11:06:37 ubuntu kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Nov 23 11:06:37 ubuntu kernel: [    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 23 11:06:37 ubuntu kernel: [    0.311777] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Nov 23 11:06:37 ubuntu kernel: [    0.311788] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 23 11:06:37 ubuntu kernel: [    0.320030] Brought up 2 CPUs
Nov 23 11:06:37 ubuntu kernel: [    0.320033] Total of 2 processors activated (6650.43 BogoMIPS).
Nov 23 11:06:37 ubuntu kernel: [    0.320087] CPU0 attaching sched-domain:
Nov 23 11:06:37 ubuntu kernel: [    0.320091]  domain 0: span 0-1 level MC
Nov 23 11:06:37 ubuntu kernel: [    0.320094]   groups: 0 1
Nov 23 11:06:37 ubuntu kernel: [    0.320100] CPU1 attaching sched-domain:
Nov 23 11:06:37 ubuntu kernel: [    0.320102]  domain 0: span 0-1 level MC
Nov 23 11:06:37 ubuntu kernel: [    0.320105]   groups: 1 0
Nov 23 11:06:37 ubuntu kernel: [    0.320196] Booting paravirtualized kernel on bare hardware
Nov 23 11:06:37 ubuntu kernel: [    0.320209] regulator: core version 0.5
Nov 23 11:06:37 ubuntu kernel: [    0.320209] Time: 16:06:29  Date: 11/23/09
Nov 23 11:06:37 ubuntu kernel: [    0.320209] NET: Registered protocol family 16
Nov 23 11:06:37 ubuntu kernel: [    0.320260] ACPI: bus type pci registered
Nov 23 11:06:37 ubuntu kernel: [    0.320345] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 12
Nov 23 11:06:37 ubuntu kernel: [    0.320349] PCI: MCFG area at e0000000 reserved in E820
Nov 23 11:06:37 ubuntu kernel: [    0.320617] PCI: Using MMCONFIG at e0000000 - e0cfffff
Nov 23 11:06:37 ubuntu kernel: [    0.320619] PCI: Using configuration type 1 for base access
Nov 23 11:06:37 ubuntu kernel: [    0.321666] bio: create slab <bio-0> at 0
Nov 23 11:06:37 ubuntu kernel: [    0.321666] ACPI: EC: Look up EC in DSDT
Nov 23 11:06:37 ubuntu kernel: [    0.330757] ACPI: BIOS _OSI(Linux) query ignored
Nov 23 11:06:37 ubuntu kernel: [    0.338712] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov 23 11:06:37 ubuntu kernel: [    0.350193] ACPI: Interpreter enabled
Nov 23 11:06:37 ubuntu kernel: [    0.350198] ACPI: (supports S0 S3 S4 S5)
Nov 23 11:06:37 ubuntu kernel: [    0.350222] ACPI: Using IOAPIC for interrupt routing
Nov 23 11:06:37 ubuntu kernel: [    0.360717] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
Nov 23 11:06:37 ubuntu kernel: [    0.360824] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
Nov 23 11:06:37 ubuntu kernel: [    0.360824] ACPI: EC: driver started in interrupt mode
Nov 23 11:06:37 ubuntu kernel: [    0.360824] ACPI: Power Resource [CTHT] (off)
Nov 23 11:06:37 ubuntu kernel: [    0.360824] ACPI: No dock devices found.
Nov 23 11:06:37 ubuntu kernel: [    0.361591] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 23 11:06:37 ubuntu kernel: [    0.361754] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Nov 23 11:06:37 ubuntu kernel: [    0.361759] pci 0000:00:04.0: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.361817] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Nov 23 11:06:37 ubuntu kernel: [    0.361821] pci 0000:00:06.0: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.361877] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Nov 23 11:06:37 ubuntu kernel: [    0.361882] pci 0000:00:07.0: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.361952] pci 0000:00:12.0: reg 10 io port: [0x8438-0x843f]
Nov 23 11:06:37 ubuntu kernel: [    0.361962] pci 0000:00:12.0: reg 14 io port: [0x8444-0x8447]
Nov 23 11:06:37 ubuntu kernel: [    0.361971] pci 0000:00:12.0: reg 18 io port: [0x8430-0x8437]
Nov 23 11:06:37 ubuntu kernel: [    0.361980] pci 0000:00:12.0: reg 1c io port: [0x8440-0x8443]
Nov 23 11:06:37 ubuntu kernel: [    0.361989] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
Nov 23 11:06:37 ubuntu kernel: [    0.361999] pci 0000:00:12.0: reg 24 32bit mmio: [0xf0209000-0xf02093ff]
Nov 23 11:06:37 ubuntu kernel: [    0.362023] pci 0000:00:12.0: set SATA to AHCI mode
Nov 23 11:06:37 ubuntu kernel: [    0.362076] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0004000-0xf0004fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362153] pci 0000:00:13.1: reg 10 32bit mmio: [0xf0005000-0xf0005fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362229] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0006000-0xf0006fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362305] pci 0000:00:13.3: reg 10 32bit mmio: [0xf0007000-0xf0007fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362384] pci 0000:00:13.4: reg 10 32bit mmio: [0xf0008000-0xf0008fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362485] pci 0000:00:13.5: reg 10 32bit mmio: [0xf0209400-0xf02094ff]
Nov 23 11:06:37 ubuntu kernel: [    0.362558] pci 0000:00:13.5: supports D1 D2
Nov 23 11:06:37 ubuntu kernel: [    0.362560] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
Nov 23 11:06:37 ubuntu kernel: [    0.362566] pci 0000:00:13.5: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.362612] pci 0000:00:14.0: reg 10 io port: [0x8410-0x841f]
Nov 23 11:06:37 ubuntu kernel: [    0.362686] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
Nov 23 11:06:37 ubuntu kernel: [    0.362696] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
Nov 23 11:06:37 ubuntu kernel: [    0.362705] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
Nov 23 11:06:37 ubuntu kernel: [    0.362714] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
Nov 23 11:06:37 ubuntu kernel: [    0.362723] pci 0000:00:14.1: reg 20 io port: [0x8420-0x842f]
Nov 23 11:06:37 ubuntu kernel: [    0.362797] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0000000-0xf0003fff]
Nov 23 11:06:37 ubuntu kernel: [    0.362856] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Nov 23 11:06:37 ubuntu kernel: [    0.362862] pci 0000:00:14.2: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.363049] pci 0000:01:05.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363059] pci 0000:01:05.0: reg 18 64bit mmio: [0xcfef0000-0xcfefffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363065] pci 0000:01:05.0: reg 20 io port: [0x9000-0x90ff]
Nov 23 11:06:37 ubuntu kernel: [    0.363088] pci 0000:01:05.0: supports D1 D2
Nov 23 11:06:37 ubuntu kernel: [    0.363124] pci 0000:01:05.2: reg 10 64bit mmio: [0xcfeec000-0xcfeeffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363195] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
Nov 23 11:06:37 ubuntu kernel: [    0.363199] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363205] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363272] pci 0000:02:00.0: reg 10 64bit mmio: [0xf0400000-0xf0403fff]
Nov 23 11:06:37 ubuntu kernel: [    0.363281] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
Nov 23 11:06:37 ubuntu kernel: [    0.363350] pci 0000:02:00.0: supports D1 D2
Nov 23 11:06:37 ubuntu kernel: [    0.363352] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 11:06:37 ubuntu kernel: [    0.363358] pci 0000:02:00.0: PME# disabled
Nov 23 11:06:37 ubuntu kernel: [    0.363432] pci 0000:00:04.0: bridge io port: [0xa000-0xafff]
Nov 23 11:06:37 ubuntu kernel: [    0.363436] pci 0000:00:04.0: bridge 32bit mmio: [0xf0400000-0xf04fffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363510] pci 0000:00:06.0: bridge io port: [0x00-0xfff]
Nov 23 11:06:37 ubuntu kernel: [    0.363515] pci 0000:00:06.0: bridge 32bit mmio: [0x000000-0x0fffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363573] pci 0000:08:00.0: reg 10 64bit mmio: [0xf0300000-0xf030ffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363727] pci 0000:00:07.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
Nov 23 11:06:37 ubuntu kernel: [    0.363811] pci 0000:00:14.4: transparent bridge
Nov 23 11:06:37 ubuntu kernel: [    0.363848] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.363991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.364088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.364172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.364306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.364348] ACPI Warning: \_SB_.PCI0.P2P_._PRT: Return Package has no elements (empty) 20090521 nspredef-434
Nov 23 11:06:37 ubuntu kernel: [    0.364368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Nov 23 11:06:37 ubuntu kernel: [    0.374058] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374203] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374344] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374485] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374624] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374764] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.374903] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.375042] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Nov 23 11:06:37 ubuntu kernel: [    0.375241] SCSI subsystem initialized
Nov 23 11:06:37 ubuntu kernel: [    0.375269] libata version 3.00 loaded.
Nov 23 11:06:37 ubuntu kernel: [    0.375269] usbcore: registered new interface driver usbfs
Nov 23 11:06:37 ubuntu kernel: [    0.375269] usbcore: registered new interface driver hub
Nov 23 11:06:37 ubuntu kernel: [    0.375269] usbcore: registered new device driver usb
Nov 23 11:06:37 ubuntu kernel: [    0.375269] ACPI: WMI: Mapper loaded
Nov 23 11:06:37 ubuntu kernel: [    0.375269] PCI: Using ACPI for IRQ routing
Nov 23 11:06:37 ubuntu kernel: [    0.375269] pci 0000:00:06.0: BAR 13: can't allocate resource
Nov 23 11:06:37 ubuntu kernel: [    0.375269] pci 0000:00:06.0: BAR 14: can't allocate resource
Nov 23 11:06:37 ubuntu kernel: [    0.400009] Bluetooth: Core ver 2.15
Nov 23 11:06:37 ubuntu kernel: [    0.400026] NET: Registered protocol family 31
Nov 23 11:06:37 ubuntu kernel: [    0.400026] Bluetooth: HCI device and connection manager initialized
Nov 23 11:06:37 ubuntu kernel: [    0.400026] Bluetooth: HCI socket layer initialized
Nov 23 11:06:37 ubuntu kernel: [    0.400026] NetLabel: Initializing
Nov 23 11:06:37 ubuntu kernel: [    0.400026] NetLabel:  domain hash size = 128
Nov 23 11:06:37 ubuntu kernel: [    0.400026] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 23 11:06:37 ubuntu kernel: [    0.400042] NetLabel:  unlabeled traffic allowed by default
Nov 23 11:06:37 ubuntu kernel: [    0.400108] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 23 11:06:37 ubuntu kernel: [    0.400114] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Nov 23 11:06:37 ubuntu kernel: [    0.440008] pnp: PnP ACPI init
Nov 23 11:06:37 ubuntu kernel: [    0.440023] ACPI: bus type pnp registered
Nov 23 11:06:37 ubuntu kernel: [    0.444148] pnp: PnP ACPI: found 11 devices
Nov 23 11:06:37 ubuntu kernel: [    0.444151] ACPI: ACPI bus type pnp unregistered
Nov 23 11:06:37 ubuntu kernel: [    0.444165] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444168] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444178] system 00:08: ioport range 0x1080-0x1080 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444182] system 00:08: ioport range 0x220-0x22f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444186] system 00:08: ioport range 0x40b-0x40b has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444189] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444192] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444195] system 00:08: ioport range 0x530-0x537 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444199] system 00:08: ioport range 0xc00-0xc01 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444202] system 00:08: ioport range 0xc14-0xc14 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444205] system 00:08: ioport range 0xc50-0xc52 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444208] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444212] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444215] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444218] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444221] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444225] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444228] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444231] system 00:08: ioport range 0x8000-0x805f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444235] system 00:08: ioport range 0x8210-0x821f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444238] system 00:08: ioport range 0xf40-0xf47 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444241] system 00:08: ioport range 0x280-0x293 has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444245] system 00:08: ioport range 0x87f-0x87f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444252] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444256] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.444259] system 00:09: iomem range 0xffb83020-0xffb8401f has been reserved
Nov 23 11:06:37 ubuntu kernel: [    0.448975] AppArmor: AppArmor Filesystem Enabled
Nov 23 11:06:37 ubuntu kernel: [    0.449027] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov 23 11:06:37 ubuntu kernel: [    0.449031] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
Nov 23 11:06:37 ubuntu kernel: [    0.449036] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
Nov 23 11:06:37 ubuntu kernel: [    0.449041] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Nov 23 11:06:37 ubuntu kernel: [    0.449047] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
Nov 23 11:06:37 ubuntu kernel: [    0.449050] pci 0000:00:04.0:   IO window: 0xa000-0xafff
Nov 23 11:06:37 ubuntu kernel: [    0.449055] pci 0000:00:04.0:   MEM window: 0xf0400000-0xf04fffff
Nov 23 11:06:37 ubuntu kernel: [    0.449058] pci 0000:00:04.0:   PREFETCH window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449062] pci 0000:00:06.0: PCI bridge, secondary bus 0000:05
Nov 23 11:06:37 ubuntu kernel: [    0.449065] pci 0000:00:06.0:   IO window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449069] pci 0000:00:06.0:   MEM window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449072] pci 0000:00:06.0:   PREFETCH window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449077] pci 0000:00:07.0: PCI bridge, secondary bus 0000:08
Nov 23 11:06:37 ubuntu kernel: [    0.449079] pci 0000:00:07.0:   IO window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449083] pci 0000:00:07.0:   MEM window: 0xf0300000-0xf03fffff
Nov 23 11:06:37 ubuntu kernel: [    0.449087] pci 0000:00:07.0:   PREFETCH window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449091] pci 0000:00:14.4: PCI bridge, secondary bus 0000:0b
Nov 23 11:06:37 ubuntu kernel: [    0.449093] pci 0000:00:14.4:   IO window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449100] pci 0000:00:14.4:   MEM window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449105] pci 0000:00:14.4:   PREFETCH window: disabled
Nov 23 11:06:37 ubuntu kernel: [    0.449123] pci 0000:00:04.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.449132] pci 0000:00:06.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.449140] pci 0000:00:07.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.449151] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449154] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449157] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
Nov 23 11:06:37 ubuntu kernel: [    0.449160] pci_bus 0000:01: resource 1 mem: [0xcfe00000-0xcfefffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449163] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449166] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
Nov 23 11:06:37 ubuntu kernel: [    0.449169] pci_bus 0000:02: resource 1 mem: [0xf0400000-0xf04fffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449172] pci_bus 0000:05: resource 0 mem: [0x0-0xfff]
Nov 23 11:06:37 ubuntu kernel: [    0.449175] pci_bus 0000:05: resource 1 mem: [0x0-0xfffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449178] pci_bus 0000:08: resource 1 mem: [0xf0300000-0xf03fffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449181] pci_bus 0000:0b: resource 3 io:  [0x00-0xffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449184] pci_bus 0000:0b: resource 4 mem: [0x000000-0xffffffffffffffff]
Nov 23 11:06:37 ubuntu kernel: [    0.449229] NET: Registered protocol family 2
Nov 23 11:06:37 ubuntu kernel: [    0.449399] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.450528] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.453607] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.454439] TCP: Hash tables configured (established 262144 bind 65536)
Nov 23 11:06:37 ubuntu kernel: [    0.454442] TCP reno registered
Nov 23 11:06:37 ubuntu kernel: [    0.454602] NET: Registered protocol family 1
Nov 23 11:06:37 ubuntu kernel: [    0.454697] Trying to unpack rootfs image as initramfs...
Nov 23 11:06:37 ubuntu kernel: [    0.501814] Switched to high resolution mode on CPU 1
Nov 23 11:06:37 ubuntu kernel: [    0.509999] Switched to high resolution mode on CPU 0
Nov 23 11:06:37 ubuntu kernel: [    0.649289] Freeing initrd memory: 6756k freed
Nov 23 11:06:37 ubuntu kernel: [    0.655013] Scanning for low memory corruption every 60 seconds
Nov 23 11:06:37 ubuntu kernel: [    0.655210] audit: initializing netlink socket (disabled)
Nov 23 11:06:37 ubuntu kernel: [    0.655235] type=2000 audit(1258992387.650:1): initialized
Nov 23 11:06:37 ubuntu kernel: [    0.667299] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 23 11:06:37 ubuntu kernel: [    0.669039] VFS: Disk quotas dquot_6.5.2
Nov 23 11:06:37 ubuntu kernel: [    0.669111] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 23 11:06:37 ubuntu kernel: [    0.669831] fuse init (API version 7.12)
Nov 23 11:06:37 ubuntu kernel: [    0.669930] msgmni has been set to 3507
Nov 23 11:06:37 ubuntu kernel: [    0.670195] alg: No test for stdrng (krng)
Nov 23 11:06:37 ubuntu kernel: [    0.670211] io scheduler noop registered
Nov 23 11:06:37 ubuntu kernel: [    0.670214] io scheduler anticipatory registered
Nov 23 11:06:37 ubuntu kernel: [    0.670217] io scheduler deadline registered
Nov 23 11:06:37 ubuntu kernel: [    0.670266] io scheduler cfq registered (default)
Nov 23 11:06:37 ubuntu kernel: [    0.670356] pci 0000:01:05.0: Boot video device
Nov 23 11:06:37 ubuntu kernel: [    0.670558]   alloc irq_desc for 24 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670561]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670573] pcieport-driver 0000:00:04.0: irq 24 for MSI/MSI-X
Nov 23 11:06:37 ubuntu kernel: [    0.670581] pcieport-driver 0000:00:04.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.670727]   alloc irq_desc for 25 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670730]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670737] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
Nov 23 11:06:37 ubuntu kernel: [    0.670745] pcieport-driver 0000:00:06.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.670885]   alloc irq_desc for 26 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670888]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.670895] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
Nov 23 11:06:37 ubuntu kernel: [    0.670902] pcieport-driver 0000:00:07.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.670999] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 23 11:06:37 ubuntu kernel: [    0.671028] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 23 11:06:37 ubuntu kernel: [    0.671896] ACPI: AC Adapter [AC] (on-line)
Nov 23 11:06:37 ubuntu kernel: [    0.672001] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Nov 23 11:06:37 ubuntu kernel: [    0.672006] ACPI: Power Button [PWRF]
Nov 23 11:06:37 ubuntu kernel: [    0.672069] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Nov 23 11:06:37 ubuntu kernel: [    0.672072] ACPI: Sleep Button [SLPB]
Nov 23 11:06:37 ubuntu kernel: [    0.672122] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Nov 23 11:06:37 ubuntu kernel: [    0.672169] ACPI: Lid Switch [LID0]
Nov 23 11:06:37 ubuntu kernel: [    0.672224] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov 23 11:06:37 ubuntu kernel: [    0.672230] ACPI: Power Button [PWRB]
Nov 23 11:06:37 ubuntu kernel: [    0.674161] fan PNP0C0B:00: registered as cooling_device0
Nov 23 11:06:37 ubuntu kernel: [    0.674168] ACPI: Fan [FAN0] (off)
Nov 23 11:06:37 ubuntu kernel: [    0.675061] ACPI: SSDT 000000006fe8bb99 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.676144] ACPI: SSDT 000000006fe8b5fc 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.678858] Monitor-Mwait will be used to enter C-1 state
Nov 23 11:06:37 ubuntu kernel: [    0.678887] Monitor-Mwait will be used to enter C-2 state
Nov 23 11:06:37 ubuntu kernel: [    0.678896] Marking TSC unstable due to TSC halts in idle
Nov 23 11:06:37 ubuntu kernel: [    0.678914] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov 23 11:06:37 ubuntu kernel: [    0.678935] processor LNXCPU:00: registered as cooling_device1
Nov 23 11:06:37 ubuntu kernel: [    0.678939] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov 23 11:06:37 ubuntu kernel: [    0.679577] ACPI: SSDT 000000006fe8bdb8 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.680178] ACPI: SSDT 000000006fe8bb14 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
Nov 23 11:06:37 ubuntu kernel: [    0.681074] ACPI: CPU1 (power states: C1[C1] C2[C2])
Nov 23 11:06:37 ubuntu kernel: [    0.681097] processor LNXCPU:01: registered as cooling_device2
Nov 23 11:06:37 ubuntu kernel: [    0.681102] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov 23 11:06:37 ubuntu kernel: [    0.687783] thermal LNXTHERM:01: registered as thermal_zone0
Nov 23 11:06:37 ubuntu kernel: [    0.687793] ACPI: Thermal Zone [TZ1] (40 C)
Nov 23 11:06:37 ubuntu kernel: [    0.689262] Linux agpgart interface v0.103
Nov 23 11:06:37 ubuntu kernel: [    0.689273] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 23 11:06:37 ubuntu kernel: [    0.690723] brd: module loaded
Nov 23 11:06:37 ubuntu kernel: [    0.691250] loop: module loaded
Nov 23 11:06:37 ubuntu kernel: [    0.691337] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Nov 23 11:06:37 ubuntu kernel: [    0.691483] ahci 0000:00:12.0: version 3.0
Nov 23 11:06:37 ubuntu kernel: [    0.691501]   alloc irq_desc for 22 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.691503]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.691511] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 23 11:06:37 ubuntu kernel: [    0.691622] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 23 11:06:37 ubuntu kernel: [    0.691626] ahci 0000:00:12.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Nov 23 11:06:37 ubuntu kernel: [    0.692079] scsi0 : ahci
Nov 23 11:06:37 ubuntu kernel: [    0.692220] scsi1 : ahci
Nov 23 11:06:37 ubuntu kernel: [    0.692305] scsi2 : ahci
Nov 23 11:06:37 ubuntu kernel: [    0.692407] scsi3 : ahci
Nov 23 11:06:37 ubuntu kernel: [    0.692545] ata1: SATA max UDMA/133 abar m1024@0xf0209000 port 0xf0209100 irq 22
Nov 23 11:06:37 ubuntu kernel: [    0.692550] ata2: SATA max UDMA/133 abar m1024@0xf0209000 port 0xf0209180 irq 22
Nov 23 11:06:37 ubuntu kernel: [    0.692554] ata3: SATA max UDMA/133 abar m1024@0xf0209000 port 0xf0209200 irq 22
Nov 23 11:06:37 ubuntu kernel: [    0.692558] ata4: SATA max UDMA/133 abar m1024@0xf0209000 port 0xf0209280 irq 22
Nov 23 11:06:37 ubuntu kernel: [    0.692952]   alloc irq_desc for 16 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.692955]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.692961] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 11:06:37 ubuntu kernel: [    0.693018] pata_atiixp 0000:00:14.1: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    0.693165] scsi4 : pata_atiixp
Nov 23 11:06:37 ubuntu kernel: [    0.693328] scsi5 : pata_atiixp
Nov 23 11:06:37 ubuntu kernel: [    0.694217] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
Nov 23 11:06:37 ubuntu kernel: [    0.694220] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
Nov 23 11:06:37 ubuntu kernel: [    0.694956] Fixed MDIO Bus: probed
Nov 23 11:06:37 ubuntu kernel: [    0.694995] PPP generic driver version 2.4.2
Nov 23 11:06:37 ubuntu kernel: [    0.695119] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 23 11:06:37 ubuntu kernel: [    0.695348]   alloc irq_desc for 19 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.695351]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.695356] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 23 11:06:37 ubuntu kernel: [    0.695401] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.695464] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
Nov 23 11:06:37 ubuntu kernel: [    0.695499] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
Nov 23 11:06:37 ubuntu kernel: [    0.695523] ehci_hcd 0000:00:13.5: debug port 1
Nov 23 11:06:37 ubuntu kernel: [    0.695541] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf0209400
Nov 23 11:06:37 ubuntu kernel: [    0.701363] ACPI: Battery Slot [CMB0] (battery present)
Nov 23 11:06:37 ubuntu kernel: [    0.710048] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
Nov 23 11:06:37 ubuntu kernel: [    0.710154] usb usb1: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    0.710189] hub 1-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    0.710198] hub 1-0:1.0: 10 ports detected
Nov 23 11:06:37 ubuntu kernel: [    0.710296] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 23 11:06:37 ubuntu kernel: [    0.710351] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 11:06:37 ubuntu kernel: [    0.710365] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.710410] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Nov 23 11:06:37 ubuntu kernel: [    0.710435] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf0004000
Nov 23 11:06:37 ubuntu kernel: [    0.770105] usb usb2: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    0.770137] hub 2-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    0.770146] hub 2-0:1.0: 2 ports detected
Nov 23 11:06:37 ubuntu kernel: [    0.770237]   alloc irq_desc for 17 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.770239]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.770245] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 11:06:37 ubuntu kernel: [    0.770257] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.770295] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Nov 23 11:06:37 ubuntu kernel: [    0.770319] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf0005000
Nov 23 11:06:37 ubuntu kernel: [    0.830099] usb usb3: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    0.830133] hub 3-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    0.830144] hub 3-0:1.0: 2 ports detected
Nov 23 11:06:37 ubuntu kernel: [    0.830231]   alloc irq_desc for 18 on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.830233]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    0.830239] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 11:06:37 ubuntu kernel: [    0.830251] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.830287] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
Nov 23 11:06:37 ubuntu kernel: [    0.830313] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf0006000
Nov 23 11:06:37 ubuntu kernel: [    0.870512] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WH01, max UDMA/33
Nov 23 11:06:37 ubuntu kernel: [    0.890104] usb usb4: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    0.890144] hub 4-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    0.890164] hub 4-0:1.0: 2 ports detected
Nov 23 11:06:37 ubuntu kernel: [    0.890420] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 11:06:37 ubuntu kernel: [    0.890434] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.890477] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
Nov 23 11:06:37 ubuntu kernel: [    0.890494] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf0007000
Nov 23 11:06:37 ubuntu kernel: [    0.910459] ata5.00: configured for UDMA/33
Nov 23 11:06:37 ubuntu kernel: [    0.950104] usb usb5: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    0.950135] hub 5-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    0.950146] hub 5-0:1.0: 2 ports detected
Nov 23 11:06:37 ubuntu kernel: [    0.950239] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 11:06:37 ubuntu kernel: [    0.950251] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 23 11:06:37 ubuntu kernel: [    0.950287] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
Nov 23 11:06:37 ubuntu kernel: [    0.950304] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf0008000
Nov 23 11:06:37 ubuntu kernel: [    1.010104] usb usb6: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    1.010134] hub 6-0:1.0: USB hub found
Nov 23 11:06:37 ubuntu kernel: [    1.010144] hub 6-0:1.0: 2 ports detected
Nov 23 11:06:37 ubuntu kernel: [    1.010211] uhci_hcd: USB Universal Host Controller Interface driver
Nov 23 11:06:37 ubuntu kernel: [    1.010349] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Nov 23 11:06:37 ubuntu kernel: [    1.013204] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 23 11:06:37 ubuntu kernel: [    1.016049] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 23 11:06:37 ubuntu kernel: [    1.016056] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 23 11:06:37 ubuntu kernel: [    1.016059] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 23 11:06:37 ubuntu kernel: [    1.016063] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 23 11:06:37 ubuntu kernel: [    1.016066] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 23 11:06:37 ubuntu kernel: [    1.016141] mice: PS/2 mouse device common for all mice
Nov 23 11:06:37 ubuntu kernel: [    1.016294] rtc_cmos 00:04: RTC can wake from S4
Nov 23 11:06:37 ubuntu kernel: [    1.016336] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Nov 23 11:06:37 ubuntu kernel: [    1.016364] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Nov 23 11:06:37 ubuntu kernel: [    1.016484] device-mapper: uevent: version 1.0.3
Nov 23 11:06:37 ubuntu kernel: [    1.016589] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 23 11:06:37 ubuntu kernel: [    1.016678] device-mapper: multipath: version 1.1.0 loaded
Nov 23 11:06:37 ubuntu kernel: [    1.016682] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 23 11:06:37 ubuntu kernel: [    1.016951] cpuidle: using governor ladder
Nov 23 11:06:37 ubuntu kernel: [    1.017056] cpuidle: using governor menu
Nov 23 11:06:37 ubuntu kernel: [    1.017524] TCP cubic registered
Nov 23 11:06:37 ubuntu kernel: [    1.017674] NET: Registered protocol family 10
Nov 23 11:06:37 ubuntu kernel: [    1.018190] lo: Disabled Privacy Extensions
Nov 23 11:06:37 ubuntu kernel: [    1.018531] NET: Registered protocol family 17
Nov 23 11:06:37 ubuntu kernel: [    1.018552] Bluetooth: L2CAP ver 2.13
Nov 23 11:06:37 ubuntu kernel: [    1.018555] Bluetooth: L2CAP socket layer initialized
Nov 23 11:06:37 ubuntu kernel: [    1.018559] Bluetooth: SCO (Voice Link) ver 0.6
Nov 23 11:06:37 ubuntu kernel: [    1.018561] Bluetooth: SCO socket layer initialized
Nov 23 11:06:37 ubuntu kernel: [    1.018602] Bluetooth: RFCOMM TTY layer initialized
Nov 23 11:06:37 ubuntu kernel: [    1.018606] Bluetooth: RFCOMM socket layer initialized
Nov 23 11:06:37 ubuntu kernel: [    1.018608] Bluetooth: RFCOMM ver 1.11
Nov 23 11:06:37 ubuntu kernel: [    1.019199] PM: Resume from disk failed.
Nov 23 11:06:37 ubuntu kernel: [    1.019213] registered taskstats version 1
Nov 23 11:06:37 ubuntu kernel: [    1.019347]   Magic number: 1:521:136
Nov 23 11:06:37 ubuntu kernel: [    1.019373] block ram1: hash matches
Nov 23 11:06:37 ubuntu kernel: [    1.019460] rtc_cmos 00:04: setting system clock to 2009-11-23 16:06:30 UTC (1258992390)
Nov 23 11:06:37 ubuntu kernel: [    1.019464] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 23 11:06:37 ubuntu kernel: [    1.019466] EDD information not available.
Nov 23 11:06:37 ubuntu kernel: [    1.025572] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Nov 23 11:06:37 ubuntu kernel: [    1.040102] ata4: SATA link down (SStatus 0 SControl 300)
Nov 23 11:06:37 ubuntu kernel: [    1.040139] ata3: SATA link down (SStatus 0 SControl 300)
Nov 23 11:06:37 ubuntu kernel: [    1.040172] ata2: SATA link down (SStatus 0 SControl 300)
Nov 23 11:06:37 ubuntu kernel: [    1.150054] usb 1-9: new high speed USB device using ehci_hcd and address 3
Nov 23 11:06:37 ubuntu kernel: [    1.220045] ata1: softreset failed (device not ready)
Nov 23 11:06:37 ubuntu kernel: [    1.220051] ata1: applying SB600 PMP SRST workaround and retrying
Nov 23 11:06:37 ubuntu kernel: [    1.389258] usb 1-9: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    1.400054] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 11:06:37 ubuntu kernel: [    1.400427] ata1.00: ATA-8: FUJITSU MHY2160BH, 0000000B, max UDMA/100
Nov 23 11:06:37 ubuntu kernel: [    1.400433] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 23 11:06:37 ubuntu kernel: [    1.400462] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 11:06:37 ubuntu kernel: [    1.400969] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 11:06:37 ubuntu kernel: [    1.400974] ata1.00: configured for UDMA/100
Nov 23 11:06:37 ubuntu kernel: [    1.420189] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2160B 0000 PQ: 0 ANSI: 5
Nov 23 11:06:37 ubuntu kernel: [    1.420324] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 23 11:06:37 ubuntu kernel: [    1.420369] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Nov 23 11:06:37 ubuntu kernel: [    1.420422] sd 0:0:0:0: [sda] Write Protect is off
Nov 23 11:06:37 ubuntu kernel: [    1.420426] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 23 11:06:37 ubuntu kernel: [    1.420475] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 11:06:37 ubuntu kernel: [    1.420620]  sda:
Nov 23 11:06:37 ubuntu kernel: [    1.424255] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WH01 PQ: 0 ANSI: 5
Nov 23 11:06:37 ubuntu kernel: [    1.435270] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 23 11:06:37 ubuntu kernel: [    1.435276] Uniform CD-ROM driver Revision: 3.20
Nov 23 11:06:37 ubuntu kernel: [    1.435416] sr 4:0:0:0: Attached scsi CD-ROM sr0
Nov 23 11:06:37 ubuntu kernel: [    1.435471] sr 4:0:0:0: Attached scsi generic sg1 type 5
Nov 23 11:06:37 ubuntu kernel: [    1.464130]  sda1 sda2 sda3
Nov 23 11:06:37 ubuntu kernel: [    1.493687] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 23 11:06:37 ubuntu kernel: [    1.540086] usb 5-2: new full speed USB device using ohci_hcd and address 2
Nov 23 11:06:37 ubuntu kernel: [    1.590159] Freeing unused kernel memory: 660k freed
Nov 23 11:06:37 ubuntu kernel: [    1.590488] Write protecting the kernel read-only data: 7580k
Nov 23 11:06:37 ubuntu kernel: [    1.826188] sky2 driver version 1.23
Nov 23 11:06:37 ubuntu kernel: [    1.838104] usb 5-2: configuration #1 chosen from 1 choice
Nov 23 11:06:37 ubuntu kernel: [    1.838367] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 11:06:37 ubuntu kernel: [    1.838385] sky2 0000:02:00.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    1.838420] sky2 0000:02:00.0: Yukon-2 FE chip revision 3
Nov 23 11:06:37 ubuntu kernel: [    1.838512]   alloc irq_desc for 27 on node 0
Nov 23 11:06:37 ubuntu kernel: [    1.838515]   alloc kstat_irqs on node 0
Nov 23 11:06:37 ubuntu kernel: [    1.838533] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
Nov 23 11:06:37 ubuntu kernel: [    1.839327] sky2 eth0: addr 00:e0:91:34:f6:62
Nov 23 11:06:37 ubuntu kernel: [    2.262826] PM: Starting manual resume from disk
Nov 23 11:06:37 ubuntu kernel: [    2.262831] PM: Resume from partition 8:3
Nov 23 11:06:37 ubuntu kernel: [    2.262833] PM: Checking hibernation image.
Nov 23 11:06:37 ubuntu kernel: [    2.263038] PM: Resume from disk failed.
Nov 23 11:06:37 ubuntu kernel: [    2.291812] EXT4-fs (sda1): barriers enabled
Nov 23 11:06:37 ubuntu kernel: [    2.310916] kjournald2 starting: pid 377, dev sda1:8, commit interval 5 seconds
Nov 23 11:06:37 ubuntu kernel: [    2.310934] EXT4-fs (sda1): delayed allocation enabled
Nov 23 11:06:37 ubuntu kernel: [    2.310941] EXT4-fs: file extents enabled
Nov 23 11:06:37 ubuntu kernel: [    2.311618] EXT4-fs: mballoc enabled
Nov 23 11:06:37 ubuntu kernel: [    2.311635] EXT4-fs (sda1): mounted filesystem with ordered data mode
Nov 23 11:06:37 ubuntu kernel: [    2.917487] type=1505 audit(1258992392.390:2): operation="profile_load" pid=398 name=/sbin/dhclient3
Nov 23 11:06:37 ubuntu kernel: [    2.918364] type=1505 audit(1258992392.390:3): operation="profile_load" pid=398 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 23 11:06:37 ubuntu kernel: [    2.918843] type=1505 audit(1258992392.390:4): operation="profile_load" pid=398 name=/usr/lib/connman/scripts/dhclient-script
Nov 23 11:06:37 ubuntu kernel: [    2.927684] type=1505 audit(1258992392.400:5): operation="profile_load" pid=399 name=/usr/sbin/mysqld-akonadi
Nov 23 11:06:37 ubuntu kernel: [    2.954311] type=1505 audit(1258992392.430:6): operation="profile_load" pid=400 name=/usr/sbin/tcpdump
Nov 23 11:06:37 ubuntu kernel: [    3.755919] Adding 1012084k swap on /dev/sda3.  Priority:-1 extents:1 across:1012084k 
Nov 23 11:06:37 ubuntu kernel: [    4.336368] EXT4-fs (sda1): internal journal on sda1:8
Nov 23 11:06:37 ubuntu kernel: [    4.742061] udev: starting version 147
Nov 23 11:06:37 ubuntu kernel: [    4.744047] EXT4-fs (sda2): barriers enabled
Nov 23 11:06:37 ubuntu kernel: [    4.754117] kjournald2 starting: pid 454, dev sda2:8, commit interval 5 seconds
Nov 23 11:06:37 ubuntu kernel: [    4.781561] EXT4-fs (sda2): internal journal on sda2:8
Nov 23 11:06:37 ubuntu kernel: [    4.781568] EXT4-fs (sda2): delayed allocation enabled
Nov 23 11:06:37 ubuntu kernel: [    4.781572] EXT4-fs: file extents enabled
Nov 23 11:06:37 ubuntu kernel: [    4.783637] EXT4-fs: mballoc enabled
Nov 23 11:06:37 ubuntu kernel: [    4.783656] EXT4-fs (sda2): mounted filesystem with ordered data mode
Nov 23 11:06:37 ubuntu kernel: [    6.029139] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
Nov 23 11:06:37 ubuntu kernel: [    6.043949] acpi device:21: registered as cooling_device3
Nov 23 11:06:37 ubuntu kernel: [    6.044762] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/device:1f/input/input6
Nov 23 11:06:37 ubuntu kernel: [    6.044825] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Nov 23 11:06:37 ubuntu kernel: [    6.098821] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 23 11:06:37 ubuntu kernel: [    6.126808] Bluetooth: Generic Bluetooth USB driver ver 0.5
Nov 23 11:06:37 ubuntu kernel: [    6.126948] usbcore: registered new interface driver btusb
Nov 23 11:06:37 ubuntu kernel: [    6.155627] lp: driver loaded but no devices found
Nov 23 11:06:37 ubuntu kernel: [    6.161187] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
Nov 23 11:06:37 ubuntu kernel: [    6.240133] cfg80211: Calling CRDA to update world regulatory domain
Nov 23 11:06:37 ubuntu kernel: [    6.261146] [drm] Initialized drm 1.1.0 20060810
Nov 23 11:06:37 ubuntu kernel: [    6.435164] Linux video capture interface: v2.00
Nov 23 11:06:37 ubuntu kernel: [    6.481021] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 23 11:06:37 ubuntu kernel: [    6.644783] [drm] radeon default to kernel modesetting DISABLED.
Nov 23 11:06:37 ubuntu kernel: [    6.645501] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 23 11:06:37 ubuntu kernel: [    6.645678] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
Nov 23 11:06:37 ubuntu kernel: [    6.663318] uvcvideo: Found UVC 1.00 device LG Webcam (0c45:62c0)
Nov 23 11:06:37 ubuntu kernel: [    6.672547] input: LG Webcam as /devices/pci0000:00/0000:00:13.5/usb1/1-9/1-9:1.0/input/input7
Nov 23 11:06:37 ubuntu kernel: [    6.672613] usbcore: registered new interface driver uvcvideo
Nov 23 11:06:37 ubuntu kernel: [    6.672617] USB Video Class driver (v0.1.0)
Nov 23 11:06:37 ubuntu kernel: [    6.703814] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 11:06:37 ubuntu kernel: [    6.784064] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Nov 23 11:06:37 ubuntu kernel: [    6.827900] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
Nov 23 11:06:37 ubuntu kernel: [    6.902061] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
Nov 23 11:06:37 ubuntu kernel: [    6.902195] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
Nov 23 11:06:37 ubuntu kernel: [    6.905427] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 23 11:06:37 ubuntu kernel: [    7.233654] cfg80211: World regulatory domain updated:
Nov 23 11:06:37 ubuntu kernel: [    7.233658] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 23 11:06:37 ubuntu kernel: [    7.233662] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 23 11:06:37 ubuntu kernel: [    7.233666] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 23 11:06:37 ubuntu kernel: [    7.233669] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 23 11:06:37 ubuntu kernel: [    7.233672] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 23 11:06:37 ubuntu kernel: [    7.233675] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 23 11:06:37 ubuntu kernel: [    7.246868] ath5k 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 23 11:06:37 ubuntu kernel: [    7.246880] ath5k 0000:08:00.0: setting latency timer to 64
Nov 23 11:06:37 ubuntu kernel: [    7.246921] ath5k 0000:08:00.0: registered as 'phy0'
Nov 23 11:06:37 ubuntu kernel: [    7.372173] ath: EEPROM regdomain: 0x60
Nov 23 11:06:37 ubuntu kernel: [    7.372177] ath: EEPROM indicates we should expect a direct regpair map
Nov 23 11:06:37 ubuntu kernel: [    7.372182] ath: Country alpha2 being used: 00
Nov 23 11:06:37 ubuntu kernel: [    7.372183] ath: Regpair used: 0x60
Nov 23 11:06:37 ubuntu kernel: [    7.455687] type=1505 audit(1258992396.930:7): operation="profile_replace" pid=771 name=/sbin/dhclient3
Nov 23 11:06:37 ubuntu kernel: [    7.456557] type=1505 audit(1258992396.930:8): operation="profile_replace" pid=771 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 23 11:06:37 ubuntu kernel: [    7.457042] type=1505 audit(1258992396.930:9): operation="profile_replace" pid=771 name=/usr/lib/connman/scripts/dhclient-script
Nov 23 11:06:37 ubuntu kernel: [    7.458989] type=1505 audit(1258992396.930:10): operation="profile_replace" pid=772 name=/usr/sbin/mysqld-akonadi
Nov 23 11:06:37 ubuntu kernel: [    7.461426] type=1505 audit(1258992396.940:11): operation="profile_replace" pid=773 name=/usr/sbin/tcpdump
Nov 23 11:06:37 ubuntu kernel: [    7.520319] phy0: Selected rate control algorithm 'minstrel'
Nov 23 11:06:37 ubuntu kernel: [    7.521147] Registered led device: ath5k-phy0::rx
Nov 23 11:06:37 ubuntu kernel: [    7.521168] Registered led device: ath5k-phy0::tx
Nov 23 11:06:37 ubuntu kernel: [    7.521173] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Nov 23 11:06:37 ubuntu kernel: [    7.562195] sky2 eth0: enabling interface
Nov 23 11:06:37 ubuntu kernel: [    7.562486] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 23 11:06:36 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov 23 11:06:37 ubuntu bluetoothd[685]: Bluetooth daemon 4.51
Nov 23 11:06:37 ubuntu bluetoothd[829]: Starting SDP server
Nov 23 11:06:37 ubuntu bluetoothd[829]: Can't load plugin /usr/lib/bluetooth/plugins/netlink.so: /usr/lib/bluetooth/plugins/netlink.so: undefined symbol: debug
Nov 23 11:06:37 ubuntu kernel: [    7.921106] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 23 11:06:37 ubuntu kernel: [    7.921110] Bluetooth: BNEP filters: protocol multicast
Nov 23 11:06:37 ubuntu bluetoothd[829]: bridge pan0 created
Nov 23 11:06:37 ubuntu kernel: [    8.147736] Bridge firewalling registered
Nov 23 11:06:37 ubuntu bluetoothd[829]: HCI dev 0 registered
Nov 23 11:06:37 ubuntu bluetoothd[829]: HCI dev 0 up
Nov 23 11:06:37 ubuntu bluetoothd[829]: Starting security manager 0
Nov 23 11:06:38 ubuntu bluetoothd[829]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Nov 23 11:06:38 ubuntu dhclient: Listening on LPF/eth0/00:e0:91:34:f6:62
Nov 23 11:06:38 ubuntu dhclient: Sending on   LPF/eth0/00:e0:91:34:f6:62
Nov 23 11:06:38 ubuntu dhclient: Sending on   Socket/fallback
Nov 23 11:06:38 ubuntu bluetoothd[829]: Adapter /org/bluez/685/hci0 has been enabled
Nov 23 11:06:38 ubuntu bluetoothd[829]: return_link_keys (sba=00:0D:F0:48:EB:7D, dba=00:04:61:80:DB:D9)
Nov 23 11:06:38 ubuntu cron[883]: (CRON) INFO (pidfile fd = 3)
Nov 23 11:06:38 ubuntu cron[961]: (CRON) STARTUP (fork ok)
Nov 23 11:06:38 ubuntu NetworkManager: <info>  starting...
Nov 23 11:06:38 ubuntu bluetoothd[829]: Failed to access HAL
Nov 23 11:06:38 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Nov 23 11:06:38 ubuntu cron[961]: (CRON) INFO (Running @reboot jobs)
Nov 23 11:06:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Nov 23 11:06:38 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Nov 23 11:06:38 ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: autoconnect
Nov 23 11:06:39 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Nov 23 11:06:39 ubuntu NetworkManager:    SCPluginIfupdown: locking wired connection setting
Nov 23 11:06:39 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (18160736) ... get_connections.
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: (18160736) ... get_connections (managed=false): return empty list.
Nov 23 11:06:39 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:08:00.0/net/wlan0, iface: wlan0)
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:08:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:08:00.0/net/wmaster0, iface: wmaster0)
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:08:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
Nov 23 11:06:39 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Nov 23 11:06:39 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 23 11:06:39 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 23 11:06:39 ubuntu NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:07.0/0000:08:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Nov 23 11:06:39 ubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k')
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): now managed
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Nov 23 11:06:39 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov 23 11:06:39 ubuntu NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov 23 11:06:39 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:39 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:39 ubuntu NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
Nov 23 11:06:39 ubuntu kernel: [   10.370435] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 11:06:39 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Nov 23 11:06:40 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 11:06:40 ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Nov 23 11:06:40 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Nov 23 11:06:40 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:40 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov 23 11:06:40 ubuntu wpa_supplicant[1049]: Failed to initiate AP scan.
Nov 23 11:06:41 ubuntu kernel: [   12.503504] [drm] Setting GART location based on new memory map
Nov 23 11:06:41 ubuntu kernel: [   12.503703] [drm] Loading RS600 Microcode
Nov 23 11:06:41 ubuntu kernel: [   12.503729] [drm] Num pipes: 1
Nov 23 11:06:41 ubuntu kernel: [   12.503735] [drm] writeback test succeeded in 1 usecs
Nov 23 11:06:42 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:06:42 ubuntu wpa_supplicant[1049]: WPS-AP-AVAILABLE 
Nov 23 11:06:43 ubuntu console-kit-daemon[884]: WARNING: Couldn't read /proc/852/environ: Failed to open file '/proc/852/environ': No such file or directory
Nov 23 11:06:44 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:06:50 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:06:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:06:57 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Wireless'
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Wireless' has security, but secrets are required.
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 23 11:06:58 ubuntu NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 ipv4
Nov 23 11:06:58 ubuntu NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 802-1x
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Wireless' has security, and secrets exist.  No new secrets needed.
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'APR1'
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov 23 11:06:58 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 11:06:58 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 23 11:06:58 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 23 11:06:58 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Nov 23 11:06:59 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:06:59 ubuntu wpa_supplicant[1049]: WPS-AP-AVAILABLE 
Nov 23 11:06:59 ubuntu wpa_supplicant[1049]: Trying to associate with 00:1d:7e:be:a2:cb (SSID='APR1' freq=2437 MHz)
Nov 23 11:06:59 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 23 11:06:59 ubuntu wpa_supplicant[1049]: Association request to the driver failed
Nov 23 11:06:59 ubuntu kernel: [   30.300970] wlan0: authenticate with AP 00:1d:7e:be:a2:cb
Nov 23 11:06:59 ubuntu wpa_supplicant[1049]: Associated with 00:1d:7e:be:a2:cb
Nov 23 11:06:59 ubuntu kernel: [   30.304394] wlan0: authenticated
Nov 23 11:06:59 ubuntu kernel: [   30.304399] wlan0: associate with AP 00:1d:7e:be:a2:cb
Nov 23 11:06:59 ubuntu kernel: [   30.306671] wlan0: RX AssocResp from 00:1d:7e:be:a2:cb (capab=0x411 status=0 aid=1)
Nov 23 11:06:59 ubuntu kernel: [   30.306676] wlan0: associated
Nov 23 11:06:59 ubuntu kernel: [   30.307516] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 23 11:06:59 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 23 11:06:59 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 23 11:07:00 ubuntu kernel: [   30.544283] Intel AES-NI instructions are not detected.
Nov 23 11:07:00 ubuntu kernel: [   30.655608] padlock: VIA PadLock not detected.
Nov 23 11:07:00 ubuntu wpa_supplicant[1049]: WPA: Key negotiation completed with 00:1d:7e:be:a2:cb [PTK=CCMP GTK=CCMP]
Nov 23 11:07:00 ubuntu wpa_supplicant[1049]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:be:a2:cb completed (auth) [id=0 id_str=]
Nov 23 11:07:00 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 23 11:07:00 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'APR1'.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 23 11:07:00 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 23 11:07:00 ubuntu NetworkManager: <info>  dhclient started with pid 1298
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 23 11:07:00 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov 23 11:07:00 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 23 11:07:00 ubuntu dhclient: All rights reserved.
Nov 23 11:07:00 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 23 11:07:00 ubuntu dhclient: 
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Nov 23 11:07:00 ubuntu dhclient: Listening on LPF/wlan0/00:15:af:52:c1:c8
Nov 23 11:07:00 ubuntu dhclient: Sending on   LPF/wlan0/00:15:af:52:c1:c8
Nov 23 11:07:00 ubuntu dhclient: Sending on   Socket/fallback
Nov 23 11:07:00 ubuntu dhclient: DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
Nov 23 11:07:00 ubuntu dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Nov 23 11:07:00 ubuntu dhclient: bound to 192.168.1.103 -- renewal in 38085 seconds.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 23 11:07:00 ubuntu NetworkManager: <info>    address 192.168.1.103
Nov 23 11:07:00 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 23 11:07:00 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Nov 23 11:07:00 ubuntu NetworkManager: <info>    hostname 'ubuntu'
Nov 23 11:07:00 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 23 11:07:00 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov 23 11:07:01 ubuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Nov 23 11:07:01 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 11:07:01 ubuntu NetworkManager: <info>  Policy set 'Wireless' (wlan0) as default for routing and DNS.
Nov 23 11:07:01 ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov 23 11:07:01 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 23 11:07:03 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:07:03 ubuntu ntpdate[1324]: adjust time server 91.189.94.4 offset -0.315007 sec
Nov 23 11:07:10 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 23 11:07:10 ubuntu kernel: [   40.870027] wlan0: no IPv6 routers present
Nov 23 11:07:20 ubuntu kernel: [   51.500413] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Nov 23 11:07:20 ubuntu kernel: [   51.501244] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:42/input10
Nov 23 11:07:20 ubuntu kernel: [   51.501362] generic-bluetooth 0005:046D:B003.0001: input,hidraw0: BLUETOOTH HID v43.20 Mouse [Logitech MX1000 mouse] on 00:0D:F0:48:EB:7D
Nov 23 11:07:29 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 11:07:36 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 11:07:41 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:07:41 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:07:42 ubuntu ntpdate[1360]: adjust time server 91.189.94.4 offset -0.291409 sec
Nov 23 11:07:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:08:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:10:03 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:11:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:13:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:14:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:14:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:14:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 11:14:39 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov 23 11:14:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 23 11:15:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 11:15:14 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:15:14 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:15:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:17:01 ubuntu CRON[1384]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 23 11:17:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:19:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:21:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 11:21:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 11:21:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 23 11:21:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 11:21:41 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 23 11:21:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:21:57 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:22:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov 23 11:22:12 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:22:12 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:23:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:25:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:27:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 11:27:29 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 11:27:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Nov 23 11:27:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:27:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 11:28:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 11:28:26 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:28:26 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:29:34 ubuntu kernel: [ 1385.449483] CE: hpet increasing min_delta_ns to 15000 nsec
Nov 23 11:29:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:31:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:32:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:33:01 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 11:33:07 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:33:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 11:33:23 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 11:33:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 11:33:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:33:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:33:56 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:33:56 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:35:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:37:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:38:23 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 11:38:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 11:38:46 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 23 11:38:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 11:39:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 11:39:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 11:39:24 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:39:24 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:39:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:41:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:43:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:45:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:46:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 11:46:34 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 11:46:45 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:46:54 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:47:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 11:47:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 11:47:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 11:47:31 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:47:31 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:47:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:49:25 ubuntu kernel: [ 2576.290032] ath5k phy0: unsupported jumbo
Nov 23 11:49:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:51:27 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 11:51:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 11:51:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 11:51:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:51:50 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 11:52:03 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:52:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 11:52:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 11:52:28 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:52:28 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:53:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:55:13 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 11:55:21 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 11:55:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 11:55:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:55:49 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 23 11:56:05 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:56:14 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:56:14 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 11:57:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:58:54 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 11:58:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 11:59:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:59:22 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 23 11:59:41 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 11:59:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 11:59:55 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 11:59:55 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 12:00:02 ubuntu wpa_supplicant[1049]: WPA: Group rekeying completed with 00:1d:7e:be:a2:cb [GTK=CCMP]
Nov 23 12:00:02 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov 23 12:00:02 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 12:01:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:03:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:05:26 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 12:05:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 12:05:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Nov 23 12:05:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:05:55 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 12:06:04 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 23 12:06:15 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 12:06:23 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 12:06:27 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 12:06:27 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 12:07:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:09:34 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 12:09:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 23 12:09:43 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 12:09:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:09:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 12:10:11 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 12:10:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 12:10:34 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov 23 12:10:35 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 12:10:35 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 12:11:43 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 12:12:41 ubuntu NetworkManager: <info>  Sleeping...
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): now unmanaged
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1298
Nov 23 12:12:41 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): cleaning up...
Nov 23 12:12:41 ubuntu NetworkManager: <info>  (wlan0): taking down device.
Nov 23 12:12:41 ubuntu kernel: [ 3972.160055] wlan0: deauthenticating by local choice (reason=3)
Nov 23 12:12:41 ubuntu wpa_supplicant[1049]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 23 12:12:41 ubuntu kernel: [ 3972.301655] wlan0: disassociating by local choice (reason=3)
Nov 23 12:12:42 ubuntu kernel: [ 3972.810153] [drm] Num pipes: 1
Nov 23 17:16:08 ubuntu kernel: [ 3974.851254] PM: Syncing filesystems ... done.
Nov 23 17:16:08 ubuntu bluetoothd[829]: Stopping security manager 0
Nov 23 17:16:08 ubuntu kernel: [ 3974.853607] PM: Preparing system for mem sleep
Nov 23 17:16:08 ubuntu kernel: [ 3974.853611] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov 23 17:16:08 ubuntu bluetoothd[829]: HCI dev 0 down
Nov 23 17:16:08 ubuntu kernel: [ 3974.854288] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov 23 17:16:08 ubuntu bluetoothd[829]: Adapter /org/bluez/685/hci0 has been disabled
Nov 23 17:16:08 ubuntu kernel: [ 3974.854331] PM: Entering mem sleep
Nov 23 17:16:08 ubuntu kernel: [ 3974.854347] Suspending console(s) (use no_console_suspend to debug)
Nov 23 17:16:08 ubuntu bluetoothd[829]: HCI dev 0 unregistered
Nov 23 17:16:08 ubuntu kernel: [ 3974.920152] btusb_bulk_complete: hci0 urb ffff88006b10e240 failed to resubmit (1)
Nov 23 17:16:08 ubuntu bluetoothd[829]: Unregister path: /org/bluez/685/hci0
Nov 23 17:16:08 ubuntu kernel: [ 3974.921144] btusb_bulk_complete: hci0 urb ffff88006b10e0c0 failed to resubmit (1)
Nov 23 17:16:08 ubuntu bluetoothd[829]: HCI dev 0 registered
Nov 23 17:16:08 ubuntu kernel: [ 3974.922142] btusb_intr_complete: hci0 urb ffff88006b10ed80 failed to resubmit (1)
Nov 23 17:16:08 ubuntu bluetoothd[829]: HCI dev 0 up
Nov 23 17:16:08 ubuntu bluetoothd[829]: Starting security manager 0
Nov 23 17:16:08 ubuntu kernel: [ 3974.980064] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 23 17:16:08 ubuntu kernel: [ 3974.980273] sd 0:0:0:0: [sda] Stopping disk
Nov 23 17:16:08 ubuntu kernel: [ 3976.341778] ACPI handle has no context!
Nov 23 17:16:08 ubuntu kernel: [ 3976.341865] ath5k 0000:08:00.0: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.360041] sky2 eth0: disabling interface
Nov 23 17:16:08 ubuntu kernel: [ 3976.360434] sky2 0000:02:00.0: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.490071] HDA Intel 0000:01:05.2: PCI INT B disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.490110] ACPI handle has no context!
Nov 23 17:16:08 ubuntu kernel: [ 3976.510034] pci 0000:01:05.0: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.620123] HDA Intel 0000:00:14.2: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640239] pata_atiixp 0000:00:14.1: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640249] ehci_hcd 0000:00:13.5: PCI INT D disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640258] ohci_hcd 0000:00:13.4: PCI INT C disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640266] ohci_hcd 0000:00:13.3: PCI INT B disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640275] ohci_hcd 0000:00:13.2: PCI INT C disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640283] ohci_hcd 0000:00:13.1: PCI INT B disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.640291] ohci_hcd 0000:00:13.0: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.720193] ahci 0000:00:12.0: PCI INT A disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.720919] PM: suspend devices took 1.870 seconds
Nov 23 17:16:08 ubuntu kernel: [ 3976.721104] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3976.960071] ACPI: Preparing to enter system sleep state S3
Nov 23 17:16:08 ubuntu kernel: [ 3976.960758] Disabling non-boot CPUs ...
Nov 23 17:16:08 ubuntu kernel: [ 3977.070017] CPU 1 is now offline
Nov 23 17:16:08 ubuntu kernel: [ 3977.070020] SMP alternatives: switching to UP code
Nov 23 17:16:08 ubuntu kernel: [ 3977.077619] CPU0 attaching NULL sched-domain.
Nov 23 17:16:08 ubuntu kernel: [ 3977.077623] CPU1 attaching NULL sched-domain.
Nov 23 17:16:08 ubuntu kernel: [ 3977.077634] CPU0 attaching NULL sched-domain.
Nov 23 17:16:08 ubuntu kernel: [ 3977.077843] CPU1 is down
Nov 23 17:16:08 ubuntu kernel: [ 3977.077852] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 23 17:16:08 ubuntu kernel: [ 3977.077852] Back to C!
Nov 23 17:16:08 ubuntu kernel: [ 3977.077852] CPU0: Thermal LVT vector (0xfa) already installed
Nov 23 17:16:08 ubuntu kernel: [ 3977.077852] Enabling non-boot CPUs ...
Nov 23 17:16:08 ubuntu kernel: [ 3977.077852] SMP alternatives: switching to SMP code
Nov 23 17:16:08 ubuntu kernel: [ 3977.085385] Booting processor 1 APIC 0x1 ip 0x6000
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] Initializing CPU#1
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] Calibrating delay using timer specific routine.. 3325.08 BogoMIPS (lpj=16625416)
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU: L2 cache: 2048K
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU 1/0x1 -> Node 0
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU: Physical Processor ID: 0
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU: Processor Core ID: 1
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] mce: CPU supports 6 MCE banks
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] CPU1: Thermal monitoring enabled (TM2)
Nov 23 17:16:08 ubuntu kernel: [ 3977.077475] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 23 17:16:08 ubuntu kernel: [ 3977.241809] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Nov 23 17:16:08 ubuntu kernel: [ 3977.241876] CPU0 attaching NULL sched-domain.
Nov 23 17:16:08 ubuntu kernel: [ 3977.242519] Switched to high resolution mode on CPU 1
Nov 23 17:16:08 ubuntu kernel: [ 3977.280026] CPU0 attaching sched-domain:
Nov 23 17:16:08 ubuntu kernel: [ 3977.280030]  domain 0: span 0-1 level MC
Nov 23 17:16:08 ubuntu kernel: [ 3977.280033]   groups: 0 1
Nov 23 17:16:08 ubuntu kernel: [ 3977.280038] CPU1 attaching sched-domain:
Nov 23 17:16:08 ubuntu kernel: [ 3977.280040]  domain 0: span 0-1 level MC
Nov 23 17:16:08 ubuntu kernel: [ 3977.280042]   groups: 1 0
Nov 23 17:16:08 ubuntu kernel: [ 3977.282519] CPU1 is up
Nov 23 17:16:08 ubuntu kernel: [ 3977.282522] ACPI: Waking up from system sleep state S3
Nov 23 17:16:08 ubuntu kernel: [ 3977.500013] Clocksource tsc unstable (delta = -419987834 ns)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370181] pcieport-driver 0000:00:04.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370190] pcieport-driver 0000:00:04.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370195] pcieport-driver 0000:00:04.0: restoring config space at offset 0x8 (was 0x0, writing 0xf040f040)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370200] pcieport-driver 0000:00:04.0: restoring config space at offset 0x7 (was 0x101, writing 0xa1a1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370204] pcieport-driver 0000:00:04.0: restoring config space at offset 0x6 (was 0x0, writing 0x40200)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370211] pcieport-driver 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370216] pcieport-driver 0000:00:04.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370249] pcieport-driver 0000:00:06.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370258] pcieport-driver 0000:00:06.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370262] pcieport-driver 0000:00:06.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370267] pcieport-driver 0000:00:06.0: restoring config space at offset 0x7 (was 0x101, writing 0x1f1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370271] pcieport-driver 0000:00:06.0: restoring config space at offset 0x6 (was 0x0, writing 0x70500)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370277] pcieport-driver 0000:00:06.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370283] pcieport-driver 0000:00:06.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100404)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370315] pcieport-driver 0000:00:07.0: restoring config space at offset 0xf (was 0xff, writing 0x400ff)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370324] pcieport-driver 0000:00:07.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370328] pcieport-driver 0000:00:07.0: restoring config space at offset 0x8 (was 0x0, writing 0xf030f030)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370333] pcieport-driver 0000:00:07.0: restoring config space at offset 0x7 (was 0x101, writing 0x200001f1)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370337] pcieport-driver 0000:00:07.0: restoring config space at offset 0x6 (was 0x0, writing 0xa0800)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370344] pcieport-driver 0000:00:07.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10008)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370349] pcieport-driver 0000:00:07.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370404] ahci 0000:00:12.0: restoring config space at offset 0x2 (was 0x1018f00, writing 0x1060100)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370428] ahci 0000:00:12.0: set SATA to AHCI mode
Nov 23 17:16:08 ubuntu kernel: [ 3978.370458] ohci_hcd 0000:00:13.0: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370495] ohci_hcd 0000:00:13.1: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370530] ohci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370566] ohci_hcd 0000:00:13.3: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370601] ohci_hcd 0000:00:13.4: restoring config space at offset 0x1 (was 0x2a00017, writing 0x2a00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370647] ehci_hcd 0000:00:13.5: restoring config space at offset 0x1 (was 0x2b00017, writing 0x2b00013)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370667] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3978.370723] pata_atiixp 0000:00:14.1: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370745] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370773] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370865] pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370892] HDA Intel 0000:01:05.2: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370925] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370943] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xa001)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370951] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0400004)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370957] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Nov 23 17:16:08 ubuntu kernel: [ 3978.370964] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 23 17:16:08 ubuntu kernel: [ 3978.371022] ath5k 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Nov 23 17:16:08 ubuntu kernel: [ 3978.371044] ath5k 0000:08:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0300004)
Nov 23 17:16:08 ubuntu kernel: [ 3978.371050] ath5k 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Nov 23 17:16:08 ubuntu kernel: [ 3978.371057] ath5k 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Nov 23 17:16:08 ubuntu kernel: [ 3981.803262] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 23 17:16:08 ubuntu kernel: [ 3981.803329] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 17:16:08 ubuntu kernel: [ 3981.830044] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 17:16:08 ubuntu kernel: [ 3981.860049] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 17:16:08 ubuntu kernel: [ 3981.890042] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 23 17:16:08 ubuntu kernel: [ 3981.920042] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 23 17:16:08 ubuntu kernel: [ 3981.950041] ehci_hcd 0000:00:13.5: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3981.950050] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 23 17:16:08 ubuntu kernel: [ 3981.950071] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 17:16:08 ubuntu kernel: [ 3981.950095] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 23 17:16:08 ubuntu kernel: [ 3981.950140] pci 0000:01:05.0: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3981.950148] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 23 17:16:08 ubuntu kernel: [ 3981.950159] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 23 17:16:08 ubuntu kernel: [ 3981.950183] sky2 0000:02:00.0: PME# disabled
Nov 23 17:16:08 ubuntu kernel: [ 3981.952586] sky2 eth0: enabling interface
Nov 23 17:16:08 ubuntu kernel: [ 3981.952594] ath5k 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 23 17:16:08 ubuntu kernel: [ 3982.130525] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov 23 17:16:08 ubuntu kernel: [ 3982.130529] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov 23 17:16:08 ubuntu kernel: [ 3982.150059] ata2: SATA link down (SStatus 0 SControl 300)
Nov 23 17:16:08 ubuntu kernel: [ 3982.150108] ata4: SATA link down (SStatus 0 SControl 300)
Nov 23 17:16:08 ubuntu kernel: [ 3982.150136] ata3: SATA link down (SStatus 0 SControl 300)
Nov 23 17:16:08 ubuntu kernel: [ 3982.170491] ata5.00: configured for UDMA/33
Nov 23 17:16:08 ubuntu kernel: [ 3982.330037] ata1: softreset failed (device not ready)
Nov 23 17:16:08 ubuntu kernel: [ 3982.330042] ata1: applying SB600 PMP SRST workaround and retrying
Nov 23 17:16:08 ubuntu kernel: [ 3982.510049] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 17:16:08 ubuntu kernel: [ 3982.510474] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 17:16:08 ubuntu kernel: [ 3982.510987] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Nov 23 17:16:08 ubuntu kernel: [ 3982.510991] ata1.00: configured for UDMA/100
Nov 23 17:16:08 ubuntu kernel: [ 3982.550045] usb 1-9: reset high speed USB device using ehci_hcd and address 3
Nov 23 17:16:08 ubuntu kernel: [ 3982.786969] sd 0:0:0:0: [sda] Starting disk
Nov 23 17:16:08 ubuntu kernel: [ 3982.950039] usb 5-2: reset full speed USB device using ohci_hcd and address 2
Nov 23 17:16:08 ubuntu kernel: [ 3983.206087] btusb 5-2:1.0: no reset_resume for driver btusb?
Nov 23 17:16:08 ubuntu kernel: [ 3983.206092] btusb 5-2:1.1: no reset_resume for driver btusb?
Nov 23 17:16:08 ubuntu kernel: [ 3983.450599] PM: resume devices took 5.080 seconds
Nov 23 17:16:08 ubuntu kernel: [ 3983.450601] ------------[ cut here ]------------
Nov 23 17:16:08 ubuntu kernel: [ 3983.450609] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:52 suspend_test_finish+0x7c/0x80()
Nov 23 17:16:08 ubuntu kernel: [ 3983.450612] Hardware name: E300-A.CPB1A9
Nov 23 17:16:08 ubuntu kernel: [ 3983.450613] Component: resume devices
Nov 23 17:16:08 ubuntu kernel: [ 3983.450615] Modules linked in: hidp cryptd aes_x86_64 aes_generic bridge stp bnep arc4 ecb ath5k snd_hda_codec_atihdmi joydev mac80211 snd_hda_codec_realtek snd_hda_intel uvcvideo led_class snd_hda_codec iptable_filter radeon ip_tables snd_hwdep videodev snd_pcm v4l1_compat ttm ath v4l2_compat_ioctl32 snd_timer snd soundcore drm snd_page_alloc x_tables i2c_piix4 i2c_algo_bit lp btusb shpchp parport cfg80211 psmouse video serio_raw output sky2
Nov 23 17:16:08 ubuntu kernel: [ 3983.450653] Pid: 1596, comm: pm-suspend Not tainted 2.6.31-14-generic #48-Ubuntu
Nov 23 17:16:08 ubuntu kernel: [ 3983.450655] Call Trace:
Nov 23 17:16:08 ubuntu kernel: [ 3983.450663]  [<ffffffff8105e788>] warn_slowpath_common+0x78/0xb0
Nov 23 17:16:08 ubuntu kernel: [ 3983.450667]  [<ffffffff8105e81c>] warn_slowpath_fmt+0x3c/0x40
Nov 23 17:16:08 ubuntu kernel: [ 3983.450671]  [<ffffffff810934dc>] suspend_test_finish+0x7c/0x80
Nov 23 17:16:08 ubuntu kernel: [ 3983.450675]  [<ffffffff81093289>] suspend_devices_and_enter+0xa9/0xe0
Nov 23 17:16:08 ubuntu kernel: [ 3983.450679]  [<ffffffff81093398>] enter_state+0xd8/0x110
Nov 23 17:16:08 ubuntu kernel: [ 3983.450682]  [<ffffffff81092952>] state_store+0x92/0x100
Nov 23 17:16:08 ubuntu kernel: [ 3983.450688]  [<ffffffff81274197>] kobj_attr_store+0x17/0x20
Nov 23 17:16:08 ubuntu kernel: [ 3983.450693]  [<ffffffff81184780>] sysfs_write_file+0xe0/0x160
Nov 23 17:16:08 ubuntu kernel: [ 3983.450698]  [<ffffffff8111ede8>] vfs_write+0xb8/0x1a0
Nov 23 17:16:08 ubuntu kernel: [ 3983.450703]  [<ffffffff8152bf74>] ? do_page_fault+0x194/0x370
Nov 23 17:16:08 ubuntu kernel: [ 3983.450707]  [<ffffffff8111f89c>] sys_write+0x4c/0x80
Nov 23 17:16:08 ubuntu kernel: [ 3983.450712]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Nov 23 17:16:08 ubuntu kernel: [ 3983.450715] ---[ end trace 3cc8ab9df446c9c8 ]---
Nov 23 17:16:08 ubuntu kernel: [ 3983.450886] PM: Finishing wakeup.
Nov 23 17:16:08 ubuntu kernel: [ 3983.450888] Restarting tasks ... done.
Nov 23 17:16:08 ubuntu bluetoothd[829]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Nov 23 17:16:08 ubuntu bluetoothd[829]: Adapter /org/bluez/685/hci0 has been enabled
Nov 23 17:16:08 ubuntu bluetoothd[829]: return_link_keys (sba=00:0D:F0:48:EB:7D, dba=00:04:61:80:DB:D9)
Nov 23 17:16:08 ubuntu NetworkManager: <info>  Waking up...
Nov 23 17:16:08 ubuntu NetworkManager: <info>  (wlan0): now managed
Nov 23 17:16:08 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov 23 17:16:08 ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Nov 23 17:16:09 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Nov 23 17:16:09 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov 23 17:16:09 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:09 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:09 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:09 ubuntu kernel: [ 3984.040615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 17:16:09 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov 23 17:16:09 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Nov 23 17:16:09 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:09 ubuntu wpa_supplicant[1049]: Failed to initiate AP scan.
Nov 23 17:16:09 ubuntu kernel: [ 3984.945596] [drm] Loading RS600 Microcode
Nov 23 17:16:09 ubuntu kernel: [ 3984.945645] [drm] Num pipes: 1
Nov 23 17:16:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:16:15 ubuntu wpa_supplicant[1049]: WPS-AP-AVAILABLE 
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Wireless'
Nov 23 17:16:15 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 23 17:16:15 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Wireless' has security, and secrets exist.  No new secrets needed.
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'APR1'
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov 23 17:16:15 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 17:16:15 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 23 17:16:15 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 23 17:16:15 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 23 17:16:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: WPS-AP-AVAILABLE 
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: Trying to associate with 00:1d:7e:be:a2:cb (SSID='APR1' freq=2437 MHz)
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: Association request to the driver failed
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: Associated with 00:1d:7e:be:a2:cb
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 23 17:16:22 ubuntu kernel: [ 3997.243507] wlan0: authenticate with AP 00:1d:7e:be:a2:cb
Nov 23 17:16:22 ubuntu kernel: [ 3997.244941] wlan0: authenticated
Nov 23 17:16:22 ubuntu kernel: [ 3997.244944] wlan0: associate with AP 00:1d:7e:be:a2:cb
Nov 23 17:16:22 ubuntu kernel: [ 3997.247109] wlan0: RX AssocResp from 00:1d:7e:be:a2:cb (capab=0x411 status=0 aid=1)
Nov 23 17:16:22 ubuntu kernel: [ 3997.247113] wlan0: associated
Nov 23 17:16:22 ubuntu kernel: [ 3997.247778] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: WPA: Key negotiation completed with 00:1d:7e:be:a2:cb [PTK=CCMP GTK=CCMP]
Nov 23 17:16:22 ubuntu wpa_supplicant[1049]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:be:a2:cb completed (auth) [id=0 id_str=]
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'APR1'.
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 23 17:16:22 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 23 17:16:22 ubuntu NetworkManager: <info>  dhclient started with pid 1819
Nov 23 17:16:22 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov 23 17:16:22 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 23 17:16:22 ubuntu dhclient: All rights reserved.
Nov 23 17:16:22 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 23 17:16:22 ubuntu dhclient: 
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 23 17:16:22 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 23 17:16:22 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Nov 23 17:16:22 ubuntu dhclient: Listening on LPF/wlan0/00:15:af:52:c1:c8
Nov 23 17:16:22 ubuntu dhclient: Sending on   LPF/wlan0/00:15:af:52:c1:c8
Nov 23 17:16:22 ubuntu dhclient: Sending on   Socket/fallback
Nov 23 17:16:25 ubuntu dhclient: DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
Nov 23 17:16:25 ubuntu dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Nov 23 17:16:25 ubuntu dhclient: bound to 192.168.1.103 -- renewal in 39889 seconds.
Nov 23 17:16:25 ubuntu NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Nov 23 17:16:25 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 23 17:16:25 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 23 17:16:25 ubuntu NetworkManager: <info>    address 192.168.1.103
Nov 23 17:16:25 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 23 17:16:25 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Nov 23 17:16:25 ubuntu NetworkManager: <info>    hostname 'ubuntu'
Nov 23 17:16:25 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Nov 23 17:16:25 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 23 17:16:25 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 23 17:16:25 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov 23 17:16:26 ubuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Nov 23 17:16:26 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 23 17:16:26 ubuntu NetworkManager: <info>  Policy set 'Wireless' (wlan0) as default for routing and DNS.
Nov 23 17:16:26 ubuntu NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov 23 17:16:26 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 23 17:16:27 ubuntu ntpdate[1836]: step time server 91.189.94.4 offset 0.822074 sec
Nov 23 17:16:33 ubuntu kernel: [ 4007.430039] wlan0: no IPv6 routers present
Nov 23 17:16:35 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:16:38 ubuntu kernel: [ 4012.485906] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:42/input11
Nov 23 17:16:38 ubuntu kernel: [ 4012.486015] generic-bluetooth 0005:046D:B003.0002: input,hidraw1: BLUETOOTH HID v43.20 Mouse [Logitech MX1000 mouse] on 00:0D:F0:48:EB:7D
Nov 23 17:17:02 ubuntu CRON[1862]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 23 17:17:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:18:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:18:24 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 17:18:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 17:18:40 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 17:18:53 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 17:19:06 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 23 17:19:19 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 17:19:25 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:19:25 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:19:35 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:21:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:23:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:24:32 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 23 17:24:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 17:24:53 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 17:25:03 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov 23 17:25:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:25:23 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 17:25:33 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:25:33 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:27:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:28:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 17:28:50 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 17:28:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Nov 23 17:29:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:29:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 17:29:30 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 17:29:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 17:29:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov 23 17:29:48 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:29:48 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:31:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:32:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 17:32:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 17:32:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 23 17:33:08 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 23 17:33:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:33:27 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Nov 23 17:33:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Nov 23 17:33:49 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:33:49 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:35:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:37:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:39:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:40:26 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 17:40:33 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 17:40:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Nov 23 17:40:59 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 17:41:06 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Nov 23 17:41:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:41:23 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 23 17:41:27 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:41:27 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:43:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:44:25 ubuntu kernel: [ 5679.868356] ath5k phy0: unsupported jumbo
Nov 23 17:45:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:45:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 23 17:45:56 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Nov 23 17:46:17 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 23 17:46:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 23 17:46:46 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 23 17:46:49 ubuntu dhclient: No DHCPOFFERS received.
Nov 23 17:46:49 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 23 17:47:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:49:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 17:51:15 ubuntu wpa_supplicant[1049]: CTRL-EVENT-SCAN-RESULTS 
```

does anything look unusual?

if the computer isn't on at 4:01am, will cron.daily simply run when the computer is turned on? if not, can i change when cron.daily is run?

---

### Post by dcstar on 2009-11-23
> **anti-destin said:**
> thanks for the reply. but that simply tells me (unless i missed something) how to configure the rotation of the log files. i didn't see anything in there about specifying when logrotate itself should be called.

from what i can tell, logrotate is supposed to be called daily by cron, but i have no idea when it is called. 12am? 7pm?
........
This package is installed by default for a good reason:
```
man anacron
```

---

### Post by anti-destin on 2009-11-30
i've been looking through the log files, and they seem to be filling up with the same sorts of messages.

for example:
```
Nov 30 20:51:36 ubuntu kernel: [34490.094018] CPU0: Temperature/speed normal
Nov 30 20:51:36 ubuntu kernel: [34490.095956] CPU0: Temperature above threshold, cpu clock throttled (total events = 1521833)
Nov 30 20:51:36 ubuntu kernel: [34490.096742] CPU0: Temperature/speed normal
Nov 30 20:51:36 ubuntu kernel: [34490.097087] CPU0: Temperature above threshold, cpu clock throttled (total events = 1521834)
Nov 30 20:51:36 ubuntu kernel: [34490.097875] CPU0: Temperature/speed normal
Nov 30 20:51:36 ubuntu kernel: [34490.099803] CPU0: Temperature above threshold, cpu clock throttled (total events = 1521835)
Nov 30 20:51:36 ubuntu kernel: [34490.100588] CPU0: Temperature/speed normal
Nov 30 20:51:36 ubuntu kernel: [34490.104212] CPU0: Temperature above threshold, cpu clock throttled (total events = 1521836)
Nov 30 20:51:36 ubuntu kernel: [34490.104993] CPU0: Temperature/speed normal
Nov 30 21:01:22 ubuntu kernel: [35075.802241] ath5k phy0: unsupported jumbo
```

also:
```
Nov 30 21:13:22 ubuntu wpa_supplicant[1046]: CTRL-EVENT-SCAN-RESULTS
Nov 30 21:13:31 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 30 21:13:45 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 30 21:13:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 30 21:14:03 ubuntu dhclient: No DHCPOFFERS received.
Nov 30 21:14:03 ubuntu dhclient: No working leases in persistent database - sleeping.
Nov 30 21:14:43 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 30 21:14:47 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 30 21:14:51 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 30 21:14:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 30 21:15:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 30 21:15:22 ubuntu wpa_supplicant[1046]: CTRL-EVENT-SCAN-RESULTS
Nov 30 21:15:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
```

i've read about the cpu temp bug. i'm guessing it will be fixed in the next version.

how about the networking entries? why do my logs get filled up with those messages?

---

