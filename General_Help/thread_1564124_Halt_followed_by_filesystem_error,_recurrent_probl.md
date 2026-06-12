---
title: "Halt followed by filesystem error, recurrent problem"
date: 2010-08-30
forum: General Help
---

### Post by leorolla on 2010-08-30
Hello fellows,

The other they my laptop totally halted in the middle of a luks-encrypted external-hd copy operation or such.

After a hard poweroff and reboot, the linux procedure would halt at the ```
(initramfs)
``` line and couldn't be pushed further.

I booted with a LiveCD, ran sudo fsck /dev/sda1 and answered yes to a bundh of filesystem-fixing prompts.

Yesterday the it happened again: freeze then incomplete boot with same error message.

Do you have an idea of what can be causing it? How can I diagnose this problem?

Thans in advance.

---

### Post by arrange on 2010-08-30
Check the SMART data, for instance in the Disk Utility programme. You can also check the */var/log/syslog* for any I/O errors. This way you can confirm or rule out a hardware error.

---

### Post by leorolla on 2010-08-31
fsck gave roughly the same results as for the first time, pasted below.

After that, it booted and Smart Data said everything is fine.

Is there a special tag I should grep from syslog?

Thanks!

```
sudo fsck /dev/sda1 -fvy
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Ubuntu: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? yes

Inode 131093 was part of the orphaned inode list.  FIXED.
Inode 131128 was part of the orphaned inode list.  FIXED.
Inode 131131 was part of the orphaned inode list.  FIXED.
Inode 131132 was part of the orphaned inode list.  FIXED.
Inode 131134 was part of the orphaned inode list.  FIXED.
Deleted inode 131143 has zero dtime.  Fix? yes

Inode 131144 was part of the orphaned inode list.  FIXED.
Inode 131145 was part of the orphaned inode list.  FIXED.
Inode 131146 was part of the orphaned inode list.  FIXED.
Inode 131147 was part of the orphaned inode list.  FIXED.
Inode 131148 was part of the orphaned inode list.  FIXED.
Inode 131169 was part of the orphaned inode list.  FIXED.
Inode 131171 was part of the orphaned inode list.  FIXED.
Inode 131178 was part of the orphaned inode list.  FIXED.
Inode 131203 was part of the orphaned inode list.  FIXED.
Inode 131205 was part of the orphaned inode list.  FIXED.
Inode 131206 was part of the orphaned inode list.  FIXED.
Inode 131208 was part of the orphaned inode list.  FIXED.
Inode 131210 was part of the orphaned inode list.  FIXED.
Inode 131212 was part of the orphaned inode list.  FIXED.
Inode 131214 was part of the orphaned inode list.  FIXED.
Inode 131215 was part of the orphaned inode list.  FIXED.
Inode 131217 was part of the orphaned inode list.  FIXED.
Inode 131218 was part of the orphaned inode list.  FIXED.
Inode 131219 was part of the orphaned inode list.  FIXED.
Inode 131221 was part of the orphaned inode list.  FIXED.
Inode 131222 was part of the orphaned inode list.  FIXED.
Inode 131224 was part of the orphaned inode list.  FIXED.
Inode 131225 was part of the orphaned inode list.  FIXED.
Inode 131226 was part of the orphaned inode list.  FIXED.
Inode 131228 was part of the orphaned inode list.  FIXED.
Inode 131233 was part of the orphaned inode list.  FIXED.
Inode 131234 was part of the orphaned inode list.  FIXED.
Inode 131236 was part of the orphaned inode list.  FIXED.
Inode 131238 was part of the orphaned inode list.  FIXED.
Inode 131240 was part of the orphaned inode list.  FIXED.
Inode 131242 was part of the orphaned inode list.  FIXED.
Inode 131243 was part of the orphaned inode list.  FIXED.
Inode 131244 was part of the orphaned inode list.  FIXED.
Inode 131245 was part of the orphaned inode list.  FIXED.
Inode 131246 was part of the orphaned inode list.  FIXED.
Inode 131247 was part of the orphaned inode list.  FIXED.
Inode 131248 was part of the orphaned inode list.  FIXED.
Inode 131250 was part of the orphaned inode list.  FIXED.
Inode 131258 was part of the orphaned inode list.  FIXED.
Inode 131266 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(99392--99430) -(327680--327734) -(327744--327804) -(327808--327847) -(328064--328105) -(338432--338498) -(338688--338799) -(338816--338931) -(339840--339912) -(340480--340597) -(340608--340734) -(340736--340813) -(340864--340910) -(340992--341071) -(341248--341378) -(343168--343256) -(343296--343434) -(347776--347870) -(347904--348047) -(348416--348562) -(351104--351204) -(353408--353511) -(356480--356588) -(532524--532533) -(533440--533449) -(533452--533453) -533455
Fix? yes

Free blocks count wrong for group #3 (4078, counted=4117).
Fix? yes

Free blocks count wrong for group #10 (8617, counted=10692).
Fix? yes

Free blocks count wrong for group #16 (20222, counted=20245).
Fix? yes

Free blocks count wrong (4440158, counted=4442295).
Fix? yes

Inode bitmap differences:  -131093 -131128 -(131131--131132) -131134 -(131143--131148) -131169 -131171 -131178 -131203 -(131205--131206) -131208 -131210 -131212 -(131214--131215) -(131217--131219) -(131221--131222) -(131224--131226) -131228 -(131233--131234) -131236 -131238 -131240 -(131242--131248) -131250 -131258 -131266
Fix? yes

Free inodes count wrong for group #16 (8000, counted=8046).
Fix? yes

Directories count wrong for group #16 (36, counted=13).
Fix? yes

Free inodes count wrong (1319176, counted=1319222).
Fix? yes


Ubuntu: ***** FILE SYSTEM WAS MODIFIED *****

  319178 inodes used (19.48%)
     255 non-contiguous files (0.1%)
     357 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 278819/91
 2108200 blocks used (32.18%)
       0 bad blocks
       1 large file

  231800 regular files
   33959 directories
      60 character device files
      26 block device files
       2 fifos
     588 links
   53256 symbolic links (40104 fast symbolic links)
      66 sockets
--------
  319757 files

```

---

### Post by arrange on 2010-08-31
Now you boot OK?
A hardware error can have something like *I/O error*, it might give a lot of matches, but we are only interested in *sda* device, not *fd* or *sr* (floppy, CDROM). Or look generally for errors connected to "ATA" or "sd" devices.

---

### Post by leorolla on 2010-08-31
There are a few interesting things in my 3 last syslogs:

- Deleting orphaned inodes during boot, mount errors in both root and home partitions.
- Clock is exactly 2 hours ahead, which is fixed when ntpd triggers time update (possibly Windows is scrambling the time, or both the LiveUSB and a Jaunty full install to another USB are scrambling the time by the same amount).
- Some messages from the network manager before the crashes.

On the next boot attempt right after the big crashes and before fixing the filesystem, nothing is written to syslog at all.

When the crashes happened I was intensely using network and reading/writing to encrypted external harddisks.

---

### Post by leorolla on 2010-09-02
Here is the part of the syslog ending at the last crash.

There are two things happening just before it:
network activity
ntpd bringing my time two hours earlier

Both happened a few minutes before the crash.

Any clue on the cause?

Thanks again.

```
Aug 28 01:52:53 leorolla-laptop kernel: [   19.761438] zd1211rw 1-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-60-b3 UW2453_RF pa0 g7---
Aug 28 01:52:53 leorolla-laptop kernel: [   19.763981] cfg80211: Calling CRDA for country: DE
Aug 28 01:52:53 leorolla-laptop cron[964]: (CRON) STARTUP (fork ok)
Aug 28 01:52:53 leorolla-laptop kernel: [   19.772560] cfg80211: Regulatory domain changed to country: DE
Aug 28 01:52:53 leorolla-laptop kernel: [   19.772569]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 28 01:52:53 leorolla-laptop kernel: [   19.772572]     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 28 01:52:53 leorolla-laptop kernel: [   19.772575]     (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 28 01:52:53 leorolla-laptop kernel: [   19.772578]     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Aug 28 01:52:53 leorolla-laptop kernel: [   19.795966] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (wlan0): preparing device.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 28 01:52:53 leorolla-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): carrier is OFF
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): now managed
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): bringing up device.
Aug 28 01:52:53 leorolla-laptop kernel: [   19.799641] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): preparing device.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: started, version 2.52 cachesize 150
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: reading /etc/resolv.conf
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: using nameserver 212.27.40.241#53
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: using nameserver 212.27.40.240#53
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: using nameserver 212.27.40.241#53
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: using nameserver 212.27.40.240#53
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  modem-manager is now available
Aug 28 01:52:53 leorolla-laptop dnsmasq[980]: read /etc/hosts - 8 addresses
Aug 28 01:52:53 leorolla-laptop cron[964]: (CRON) INFO (Running @reboot jobs)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Trying to start the supplicant...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) starting connection 'Auto Ethernet'
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  dhclient started with pid 988
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Aug 28 01:52:53 leorolla-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 28 01:52:53 leorolla-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 28 01:52:53 leorolla-laptop dhclient: All rights reserved.
Aug 28 01:52:53 leorolla-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 28 01:52:53 leorolla-laptop dhclient: 
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Aug 28 01:52:53 leorolla-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 28 01:52:53 leorolla-laptop dhclient: Listening on LPF/eth0/00:40:d0:c0:e8:98
Aug 28 01:52:53 leorolla-laptop dhclient: Sending on   LPF/eth0/00:40:d0:c0:e8:98
Aug 28 01:52:53 leorolla-laptop dhclient: Sending on   Socket/fallback
Aug 28 01:52:53 leorolla-laptop anacron[951]: Will run job `cron.daily' in 5 min.
Aug 28 01:52:53 leorolla-laptop anacron[951]: Jobs will be executed sequentially
Aug 28 01:52:53 leorolla-laptop acpid: client connected from 1006[0:0]
Aug 28 01:52:53 leorolla-laptop acpid: 1 client rule loaded
Aug 28 01:52:54 leorolla-laptop kernel: [   20.282718] [drm] Initialized drm 1.1.0 20060810
Aug 28 01:52:54 leorolla-laptop wpa_supplicant[986]: WPS-AP-AVAILABLE 
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Tarsila'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tarsila' has security, and secrets exist.  No new secrets needed.
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'ssid' value 'Tarsila'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 28 01:52:54 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 28 01:52:54 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 28 01:52:54 leorolla-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 28 01:52:55 leorolla-laptop avahi-daemon[795]: Registering new address record for fe80::240:d0ff:fec0:e898 on eth0.*.
Aug 28 01:52:56 leorolla-laptop dhclient: DHCPREQUEST of 192.168.0.55 on eth0 to 255.255.255.255 port 67
Aug 28 01:52:56 leorolla-laptop dhclient: DHCPACK of 192.168.0.55 from 192.168.0.254
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully called chroot.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully dropped privileges.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully limited resources.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Running.
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>    address 192.168.0.55
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>    gateway 192.168.0.254
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>    nameserver '212.27.40.240'
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>    nameserver '212.27.40.241'
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Watchdog thread running.
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 28 01:52:56 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 28 01:52:56 leorolla-laptop avahi-daemon[795]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.55.
Aug 28 01:52:56 leorolla-laptop avahi-daemon[795]: New relevant interface eth0.IPv4 for mDNS.
Aug 28 01:52:56 leorolla-laptop avahi-daemon[795]: Registering new address record for 192.168.0.55 on eth0.IPv4.
Aug 28 01:52:56 leorolla-laptop dhclient: bound to 192.168.0.55 -- renewal in 431890 seconds.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Canary thread running.
Aug 28 01:52:56 leorolla-laptop polkitd[1080]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1071 of process 1071 (n/a) owned by '114' high priority at nice level -11.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Supervising 1 threads of 1 processes of 1 users.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1121 of process 1071 (n/a) owned by '114' RT at priority 5.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Supervising 2 threads of 1 processes of 1 users.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1122 of process 1071 (n/a) owned by '114' RT at priority 5.
Aug 28 01:52:56 leorolla-laptop rtkit-daemon[1073]: Supervising 3 threads of 1 processes of 1 users.
Aug 28 01:52:56 leorolla-laptop gdm-simple-greeter[1064]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 28 01:52:57 leorolla-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug 28 01:52:57 leorolla-laptop NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS.
Aug 28 01:52:57 leorolla-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 28 01:52:57 leorolla-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 28 01:52:57 leorolla-laptop acpid: client connected from 1169[108:114]
Aug 28 01:52:57 leorolla-laptop acpid: 1 client rule loaded
Aug 28 01:52:57 leorolla-laptop kernel: [   23.654201] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Aug 27 23:52:56 leorolla-laptop ntpdate[1238]: step time server 91.189.94.4 offset -7201.168685 sec
Aug 27 23:52:56 leorolla-laptop ntpd[1310]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 00:28:40 UTC 2010 (1)
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: precision = 1.000 usec
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #2 eth0, fe80::240:d0ff:fec0:e898#123 Enabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #3 lo, ::1#123 Enabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: Listening on interface #5 eth0, 192.168.0.55#123 Enabled
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: kernel time sync status 2040
Aug 27 23:52:56 leorolla-laptop ntpd[1314]: frequency initialized -196.918 PPM from /var/lib/ntp/ntp.drift
Aug 27 23:52:56 leorolla-laptop gdm-simple-greeter[1064]: WARNING: Unable to parse history: (null)   15#012
Aug 27 23:52:56 leorolla-laptop gdm-simple-greeter[1064]: WARNING: Unable to parse history: (null)   3#012
Aug 27 23:52:57 leorolla-laptop postfix/master[1366]: daemon started -- version 2.7.0, configuration /etc/postfix
Aug 27 23:52:57 leorolla-laptop kernel: [   24.729854] ppdev: user-space parallel port driver
Aug 27 23:52:57 leorolla-laptop init: plymouth-stop pre-start process (1534) terminated with status 1
Aug 27 23:53:02 leorolla-laptop kernel: [   30.280040] eth0: no IPv6 routers present
Aug 27 23:53:04 leorolla-laptop gdm-session-worker[1068]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 27 23:53:12 leorolla-laptop gdm-session-worker[1068]: pam_sm_authenticate: Called
Aug 27 23:53:12 leorolla-laptop gdm-session-worker[1068]: pam_sm_authenticate: username = [anaclara]
Aug 27 23:53:12 leorolla-laptop gdm-session-worker[1539]: Passphrase file wrapped
Aug 27 23:53:14 leorolla-laptop NetworkManager: <info>  wlan0: link timed out.
Aug 27 23:53:15 leorolla-laptop kernel: [   42.643227] padlock: VIA PadLock not detected.
Aug 27 23:53:16 leorolla-laptop gdm-session-worker[1576]: WARNING: Could not copy file to cache: Error opening file '/var/cache/gdm/anaclara/dmrc': Permission denied
Aug 27 23:53:17 leorolla-laptop gnome-session[1576]: WARNING: Could not parse desktop file /home/anaclara/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
Aug 27 23:53:17 leorolla-laptop gnome-session[1576]: WARNING: could not read /home/anaclara/.config/autostart/xfconf-migration-4.6.desktop
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1647 of process 1647 (n/a) owned by '1001' high priority at nice level -11.
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Supervising 4 threads of 2 processes of 2 users.
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1661 of process 1647 (n/a) owned by '1001' RT at priority 5.
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Supervising 5 threads of 2 processes of 2 users.
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1662 of process 1647 (n/a) owned by '1001' RT at priority 5.
Aug 27 23:53:18 leorolla-laptop rtkit-daemon[1073]: Supervising 6 threads of 2 processes of 2 users.
Aug 27 23:53:19 leorolla-laptop rtkit-daemon[1073]: Sucessfully made thread 1666 of process 1666 (n/a) owned by '1001' high priority at nice level -11.
Aug 27 23:53:19 leorolla-laptop rtkit-daemon[1073]: Supervising 7 threads of 3 processes of 2 users.
Aug 27 23:53:19 leorolla-laptop pulseaudio[1666]: pid.c: Daemon already running.
Aug 27 23:53:48 leorolla-laptop gnome-session[1576]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: Failed to execute child process "/usr/lib/evolution/2.28/evolution-alarm-notify" (No such file or directory)
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tarsila' has security, and secrets exist.  No new secrets needed.
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'ssid' value 'Tarsila'
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 27 23:53:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:53:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 27 23:53:59 leorolla-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 27 23:54:16 leorolla-laptop kernel: [  103.560088] usb 1-3: new high speed USB device using ehci_hcd and address 5
Aug 27 23:54:16 leorolla-laptop kernel: [  103.712988] usb 1-3: configuration #1 chosen from 1 choice
Aug 27 23:54:16 leorolla-laptop kernel: [  103.817289] Initializing USB Mass Storage driver...
Aug 27 23:54:16 leorolla-laptop kernel: [  103.817683] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 27 23:54:16 leorolla-laptop kernel: [  103.818093] usbcore: registered new interface driver usb-storage
Aug 27 23:54:16 leorolla-laptop kernel: [  103.818101] USB Mass Storage support registered.
Aug 27 23:54:16 leorolla-laptop kernel: [  103.824636] usb-storage: device found at 5
Aug 27 23:54:16 leorolla-laptop kernel: [  103.824642] usb-storage: waiting for device to settle before scanning
Aug 27 23:54:21 leorolla-laptop kernel: [  108.824430] usb-storage: device scan complete
Aug 27 23:54:21 leorolla-laptop kernel: [  108.828406] scsi 4:0:0:0: Direct-Access     Hitachi  HTS545050B9A300       PQ: 0 ANSI: 2
Aug 27 23:54:21 leorolla-laptop kernel: [  108.835222] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 27 23:54:21 leorolla-laptop kernel: [  108.838175] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Aug 27 23:54:21 leorolla-laptop kernel: [  108.840685] sd 4:0:0:0: [sdb] Write Protect is off
Aug 27 23:54:21 leorolla-laptop kernel: [  108.840693] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
Aug 27 23:54:21 leorolla-laptop kernel: [  108.840697] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 27 23:54:21 leorolla-laptop kernel: [  108.844179] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 27 23:54:21 leorolla-laptop kernel: [  108.844197]  sdb: sdb1 sdb2
Aug 27 23:54:21 leorolla-laptop kernel: [  108.874050] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 27 23:54:21 leorolla-laptop kernel: [  108.874060] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 27 23:54:25 leorolla-laptop AptDaemon: INFO: Initializing daemon
Aug 27 23:54:31 leorolla-laptop kernel: [  118.438407] padlock: VIA PadLock Hash Engine not detected.
Aug 27 23:54:31 leorolla-laptop modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-24-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Aug 27 23:54:48 leorolla-laptop kernel: [  136.253667] EXT4-fs (dm-0): warning: maximal mount count reached, running e2fsck is recommended
Aug 27 23:54:48 leorolla-laptop kernel: [  136.288884] EXT4-fs (dm-0): recovery complete
Aug 27 23:54:48 leorolla-laptop kernel: [  136.289685] EXT4-fs (dm-0): mounted filesystem with ordered data mode
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tarsila' has security, and secrets exist.  No new secrets needed.
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'ssid' value 'Tarsila'
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 27 23:54:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:54:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 27 23:54:59 leorolla-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tarsila' has security, and secrets exist.  No new secrets needed.
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'ssid' value 'Tarsila'
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 27 23:55:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:55:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 27 23:55:59 leorolla-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Tarsila' has security, and secrets exist.  No new secrets needed.
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'ssid' value 'Tarsila'
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 27 23:56:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:56:59 leorolla-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 27 23:56:59 leorolla-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 27 23:57:15 leorolla-laptop ntpd[1314]: synchronized to 91.189.94.4, stratum 2
Aug 27 23:57:15 leorolla-laptop ntpd[1314]: kernel time sync status change 2001
Aug 27 23:57:52 leorolla-laptop anacron[951]: Job `cron.daily' started
Aug 27 23:57:52 leorolla-laptop anacron[1955]: Updated timestamp for job `cron.daily' to 2010-08-27
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Tarsila)
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  Marking connection 'Auto Tarsila' invalid.
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 27 23:57:59 leorolla-laptop NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS.
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Tarsila'
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Tarsila' has security, but secrets are required.
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 27 23:58:02 leorolla-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 27 23:58:08 leorolla-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="766" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 27 23:58:40 leorolla-laptop anacron[951]: Job `cron.daily' terminated
Aug 27 23:58:40 leorolla-laptop anacron[951]: Normal exit (1 job run)
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Tarsila)
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  Marking connection 'Auto Tarsila' invalid.
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  Activation (wlan0) failed.
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug 27 23:58:54 leorolla-laptop NetworkManager: <info>  Policy set 'Auto Ethernet' (eth0) as default for routing and DNS.
Aug 27 23:59:26 leorolla-laptop AptDaemon: INFO: Quiting due to inactivity
Aug 27 23:59:26 leorolla-laptop AptDaemon: INFO: Shutdown was requested
Aug 31 12:46:50 leorolla-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 31 12:46:50 leorolla-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="775" x-info="http://www.rsyslog.com"] (re)start
Aug 31 12:46:50 leorolla-laptop rsyslogd: rsyslogd's groupid changed to 103
Aug 31 12:46:50 leorolla-laptop rsyslogd: rsyslogd's userid changed to 101
Aug 31 12:46:50 leorolla-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 31 12:46:50 leorolla-laptop init: ubiquity main process (794) terminated with status 1
Aug 31 12:46:50 leorolla-laptop NetworkManager: <info>  starting...
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Aug 31 12:46:50 leorolla-laptop NetworkManager: <info>  Trying to start the modem-manager...
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: Successfully dropped root privileges.
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: avahi-daemon 0.6.25 starting up.
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: Successfully called chroot().
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: Successfully dropped remaining capabilities.
Aug 31 12:46:50 leorolla-laptop modem-manager: Loaded plugin Nokia
Aug 31 12:46:50 leorolla-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Aug 31 12:46:50 leorolla-laptop modem-manager: Loaded plugin Sierra
Aug 31 12:46:50 leorolla-laptop avahi-daemon[803]: No service file found in /etc/avahi/services.
Aug 31 12:46:50 leorolla-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname

```

---

### Post by leorolla on 2010-09-02
I should mention that both crashes happened last week.

I booted my WindowsXP partition a couple of times to initialize and backup an iPhone, exactly last week as well.

So this suggests to me that it can be the ntpd pulling back the clock by two hours. Can you tell anything from the syslog?

Thanks.

Edit:
The surviving part of syslog from the first crash:

```
Aug 23 20:46:57 leorolla-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="747" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 23 20:47:19 leorolla-laptop ntpd[1674]: synchronized to 91.189.94.4, stratum 2
Aug 23 20:47:19 leorolla-laptop ntpd[1674]: kernel time sync status change 2001
Aug 23 20:47:25 leorolla-laptop anacron[1004]: Job `cron.daily' terminated
Aug 23 20:47:25 leorolla-laptop anacron[1004]: Normal exit (1 job run)
Aug 23 21:04:01 leorolla-laptop sudo: pam_sm_authenticate: Called
Aug 23 21:04:01 leorolla-laptop sudo: pam_sm_authenticate: username = [leorolla]
Aug 23 21:04:01 leorolla-laptop sudo: pam_sm_authenticate: /home/leorolla is already mounted
```

I rebooted right after but "/" was not mounted nothing was written to syslog. Next entry in syslog is after fixing the filesystem from a LiveUSB.

---

