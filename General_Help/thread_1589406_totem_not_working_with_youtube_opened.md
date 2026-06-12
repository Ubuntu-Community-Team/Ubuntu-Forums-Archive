---
title: "totem not working with youtube opened"
date: 2010-10-06
forum: General Help
---

### Post by c2tarun on 2010-10-06
hi friends
i m facing a strange problem
whenever i play a video in youtube and pause it for full buffering, during that time my totem player, vlc, mplayer all stop working. they all start working after restart??
why so???

---

### Post by FahadMKS on 2010-10-06
This seems to be a strange problem.
I tried and have found no issues such as this.
Did you restarted the computer and check for the issue, If so, you may update the Ubuntu and make sure that all the updates are installed and then restart the computer again and check for the issue.

---

### Post by etdsbastar on 2010-10-06
> **c2tarun said:**
> hi friends
i m facing a strange problem
whenever i play a video in youtube and pause it for full buffering, during that time my totem player, vlc, mplayer all stop working. they all start working after restart??
why so???

Please open your browser; open youtube and then stream any video.
Meanwhile open totem; (if it not opens; let it be "as it is")

Now goto to System->Administrator->Log File Viewer and post the last 10 lines here.

It will help us to solve your problem in a much efficient way?

Thanks.

---

### Post by c2tarun on 2010-10-07
there are many log files.
which log file do you want??

---

### Post by etdsbastar on 2010-10-07
> **c2tarun said:**
> there are many log files.
which log file do you want??

messages.log, system.log and daemon.log

Thanks

---

### Post by c2tarun on 2010-10-08
> **etdsbastar said:**
> messages.log, system.log and daemon.log

Thanks


messages.log

```


Oct  9 06:25:09 tarun-laptop kernel: [   16.360478] Bluetooth: RFCOMM socket layer initialized
Oct  9 06:25:09 tarun-laptop kernel: [   16.360481] Bluetooth: RFCOMM ver 1.11
Oct  9 06:25:10 tarun-laptop kernel: [   16.464656] [fglrx] Firegl kernel thread PID: 1199
Oct  9 06:25:10 tarun-laptop kernel: [   16.464842] [fglrx] IRQ 34 Enabled
Oct  9 06:25:10 tarun-laptop kernel: [   16.556391] input: PS/2  Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Oct  9 06:25:10 tarun-laptop kernel: [   16.851289] [fglrx] Gart USWC size:919 M.
Oct  9 06:25:10 tarun-laptop kernel: [   16.851293] [fglrx] Gart cacheable size:364 M.
Oct  9 06:25:10 tarun-laptop kernel: [   16.851297] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Oct  9 06:25:10 tarun-laptop kernel: [   16.851300] [fglrx] Reserved FB block: Unshared offset:fa1f000, size:2e1000 
Oct  9 06:25:10 tarun-laptop kernel: [   16.851302] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Oct  9 06:25:14 tarun-laptop kernel: [   20.579399] hda-intel: IRQ  timing workaround is activated for card #1. Suggest a bigger  bdl_pos_adj.
Oct  9 06:25:25 tarun-laptop kernel: [   31.671661] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Oct  9 06:41:41 tarun-laptop kernel: [ 1006.297199] EXT4-fs (sda4):  warning: maximal mount count reached, running e2fsck is recommended
Oct  9 06:41:41 tarun-laptop kernel: [ 1006.317099] EXT4-fs (sda4): mounted filesystem with ordered data mode
Oct  9 06:41:52 tarun-laptop pulseaudio[1435]: ratelimit.c: 12 events suppressed
Oct  9 06:58:59 tarun-laptop rsyslogd: [origin software="rsyslogd"  swVersion="4.2.0" x-pid="891" x-info="http://www.rsyslog.com"] rsyslogd  was HUPed, type 'lightweight'.

```



syslog


```
Oct  9 06:25:32 tarun-laptop dhclient: DHCPACK of 192.168.0.104 from 192.168.0.1
Oct  9 06:25:32 tarun-laptop dhclient: bound to 192.168.0.104 -- renewal in 41121 seconds.
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    address 192.168.0.104
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    gateway 192.168.0.1
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.104.
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: New relevant interface eth1.IPv4 for mDNS.
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: Registering new address record for 192.168.0.104 on eth1.IPv4.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct  9 06:25:33 tarun-laptop NetworkManager: <debug> [1286585733.047539] periodic_update(): Roamed from BSSID 00:26:5A:B3:E1:8E (xaero) to (none) ((none))
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Policy set 'Auto xaero' (eth1) as default for routing and DNS.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct  9 06:25:39 tarun-laptop ntpdate[1605]: no server suitable for synchronization found
Oct  9 06:26:11 tarun-laptop kernel: [   77.368428] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:11 tarun-laptop kernel: [   77.577538] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:11 tarun-laptop kernel: [   77.753237] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:11 tarun-laptop kernel: [   77.938522] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:11 tarun-laptop kernel: [   78.114510] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:11 tarun-laptop kernel: [   78.304457] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:12 tarun-laptop kernel: [   78.474576] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:12 tarun-laptop kernel: [   78.665511] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:12 tarun-laptop kernel: [   78.845311] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:12 tarun-laptop kernel: [   79.036100] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:12 tarun-laptop kernel: [   79.221423] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:13 tarun-laptop kernel: [   79.392466] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:13 tarun-laptop kernel: [   79.576850] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:13 tarun-laptop kernel: [   79.767836] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:13 tarun-laptop kernel: [   79.962653] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:13 tarun-laptop kernel: [   80.147699] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:14 tarun-laptop kernel: [   80.337952] [fglrx:firegl_acpi_video_event] *ERROR* Could not find private acpi context by video busid: LCD
Oct  9 06:26:28 tarun-laptop AptDaemon: INFO: Initializing daemon
Oct  9 06:30:09 tarun-laptop anacron[1068]: Job `cron.daily' started
Oct  9 06:30:09 tarun-laptop anacron[5655]: Updated timestamp for job `cron.daily' to 2010-10-09
Oct  9 06:31:29 tarun-laptop AptDaemon: INFO: Quiting due to inactivity
Oct  9 06:31:29 tarun-laptop AptDaemon: INFO: Shutdown was requested
Oct  9 06:41:41 tarun-laptop kernel: [ 1006.297199] EXT4-fs (sda4): warning: maximal mount count reached, running e2fsck is recommended
Oct  9 06:41:41 tarun-laptop kernel: [ 1006.317099] EXT4-fs (sda4): mounted filesystem with ordered data mode
Oct  9 06:41:52 tarun-laptop pulseaudio[1435]: ratelimit.c: 12 events suppressed
Oct  9 06:42:52 tarun-laptop AptDaemon: INFO: Initializing daemon
Oct  9 06:48:52 tarun-laptop AptDaemon: INFO: Quiting due to inactivity
Oct  9 06:48:52 tarun-laptop AptDaemon: INFO: Shutdown was requested
Oct  9 06:49:39 tarun-laptop pulseaudio[1435]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Oct  9 06:50:10 tarun-laptop pulseaudio[1435]: last message repeated 4 times

```



deamon.log



```
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Sucessfully called chroot.
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Sucessfully dropped privileges.
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Sucessfully limited resources.
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Running.
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Watchdog thread running.
Oct  9 06:25:12 tarun-laptop rtkit-daemon[1293]: Canary thread running.
Oct  9 06:25:12 tarun-laptop polkitd[1297]: started daemon version 0.96 using authority implementation `local' version `0.96'
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1291 of process 1291 (n/a) owned by '114' high priority at nice level -11.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Supervising 1 threads of 1 processes of 1 users.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1298 of process 1291 (n/a) owned by '114' RT at priority 5.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Supervising 2 threads of 1 processes of 1 users.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1339 of process 1291 (n/a) owned by '114' RT at priority 5.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Supervising 3 threads of 1 processes of 1 users.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1340 of process 1291 (n/a) owned by '114' RT at priority 5.
Oct  9 06:25:13 tarun-laptop rtkit-daemon[1293]: Supervising 4 threads of 1 processes of 1 users.
Oct  9 06:25:14 tarun-laptop gdm-simple-greeter[1283]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Oct  9 06:25:14 tarun-laptop gdm-session-worker[1285]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct  9 06:25:14 tarun-laptop wpa_supplicant[1137]: WPS-AP-AVAILABLE 
Oct  9 06:25:17 tarun-laptop gdm-session-worker[1350]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct  9 06:25:24 tarun-laptop gnome-session[1372]: EggSMClient-WARNING: Desktop file '/home/tarun/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1435 of process 1435 (n/a) owned by '1000' high priority at nice level -11.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Supervising 5 threads of 2 processes of 2 users.
Oct  9 06:25:25 tarun-laptop gnome-session[1372]: WARNING: Could not launch application '10a8b0faf56363e8f1128635758848782500000013790035.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1454 of process 1435 (n/a) owned by '1000' RT at priority 5.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Supervising 6 threads of 2 processes of 2 users.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto xaero'
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto xaero' has security, but secrets are required.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto xaero' has security, and secrets exist.  No new secrets needed.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Config: added 'ssid' value 'xaero'
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct  9 06:25:25 tarun-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  9 06:25:25 tarun-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct  9 06:25:25 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1461 of process 1435 (n/a) owned by '1000' RT at priority 5.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Supervising 7 threads of 2 processes of 2 users.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1467 of process 1435 (n/a) owned by '1000' RT at priority 5.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Supervising 8 threads of 2 processes of 2 users.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Sucessfully made thread 1469 of process 1469 (n/a) owned by '1000' high priority at nice level -11.
Oct  9 06:25:25 tarun-laptop rtkit-daemon[1293]: Supervising 9 threads of 3 processes of 2 users.
Oct  9 06:25:30 tarun-laptop wpa_supplicant[1137]: WPS-AP-AVAILABLE 
Oct  9 06:25:30 tarun-laptop wpa_supplicant[1137]: Trying to associate with 00:26:5a:b3:e1:8e (SSID='xaero' freq=2452 MHz)
Oct  9 06:25:30 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Oct  9 06:25:30 tarun-laptop wpa_supplicant[1137]: Association request to the driver failed
Oct  9 06:25:31 tarun-laptop wpa_supplicant[1137]: Associated with 00:26:5a:b3:e1:8e
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Oct  9 06:25:31 tarun-laptop wpa_supplicant[1137]: WPA: Key negotiation completed with 00:26:5a:b3:e1:8e [PTK=CCMP GTK=TKIP]
Oct  9 06:25:31 tarun-laptop wpa_supplicant[1137]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:b3:e1:8e completed (auth) [id=0 id_str=]
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'xaero'.
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  dhclient started with pid 1559
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Oct  9 06:25:31 tarun-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct  9 06:25:31 tarun-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct  9 06:25:31 tarun-laptop dhclient: All rights reserved.
Oct  9 06:25:31 tarun-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  9 06:25:31 tarun-laptop dhclient: 
Oct  9 06:25:31 tarun-laptop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Oct  9 06:25:31 tarun-laptop dhclient: Listening on LPF/eth1/70:f1:a1:fa:65:94
Oct  9 06:25:31 tarun-laptop dhclient: Sending on   LPF/eth1/70:f1:a1:fa:65:94
Oct  9 06:25:31 tarun-laptop dhclient: Sending on   Socket/fallback
Oct  9 06:25:32 tarun-laptop dhclient: DHCPREQUEST of 192.168.0.104 on eth1 to 255.255.255.255 port 67
Oct  9 06:25:32 tarun-laptop dhclient: DHCPACK of 192.168.0.104 from 192.168.0.1
Oct  9 06:25:32 tarun-laptop dhclient: bound to 192.168.0.104 -- renewal in 41121 seconds.
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    address 192.168.0.104
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    gateway 192.168.0.1
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  9 06:25:32 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.104.
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: New relevant interface eth1.IPv4 for mDNS.
Oct  9 06:25:32 tarun-laptop avahi-daemon[913]: Registering new address record for 192.168.0.104 on eth1.IPv4.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct  9 06:25:33 tarun-laptop NetworkManager: <debug> [1286585733.047539] periodic_update(): Roamed from BSSID 00:26:5A:B3:E1:8E (xaero) to (none) ((none))
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Policy set 'Auto xaero' (eth1) as default for routing and DNS.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct  9 06:25:33 tarun-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct  9 06:25:39 tarun-laptop ntpdate[1605]: no server suitable for synchronization found
Oct  9 06:26:28 tarun-laptop AptDaemon: INFO: Initializing daemon
Oct  9 06:31:29 tarun-laptop AptDaemon: INFO: Quiting due to inactivity
Oct  9 06:31:29 tarun-laptop AptDaemon: INFO: Shutdown was requested
Oct  9 06:42:52 tarun-laptop AptDaemon: INFO: Initializing daemon
Oct  9 06:48:52 tarun-laptop AptDaemon: INFO: Quiting due to inactivity
Oct  9 06:48:52 tarun-laptop AptDaemon: INFO: Shutdown was requested
Oct  9 07:01:26 tarun-laptop wpa_supplicant[1137]: WPA: Group rekeying completed with 00:26:5a:b3:e1:8e [GTK=TKIP]
Oct  9 07:01:26 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Oct  9 07:01:26 tarun-laptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed

```

---

### Post by etdsbastar on 2010-10-09
There is some driver and alsa-plugin bug in your machine as I see through your log files. 

Do these things :

Goto system->admniistration->hardware drivers

search for any drivers present which have no hardware installed and install it accordingly. 

Secondly, please check through synaptic that which flash plugin is installed in your machine/laptop. 

Better to use flashplugin-installer

This package automatically downloads latest flash runtime from adobe's website. If already install then please remove it completely and reinstall it and then again check for the problems after restarting your machine once.

Hope this works.

---

