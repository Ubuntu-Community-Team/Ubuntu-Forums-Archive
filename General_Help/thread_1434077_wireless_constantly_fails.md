---
title: "wireless constantly fails"
date: 2010-03-19
forum: General Help
---

### Post by serious7 on 2010-03-19
Hi for some reason my wireless is constantly failing. the only solution is a reboot but it will start to fail again. I use hp mini 210 ubuntu netbook remix.

here is a log file
----------------------
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto nicky' has security, and secrets exist.  No new secrets needed.
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'ssid' value 'nicky'
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Mar 19 19:37:37 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 19:37:37 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 19 19:37:37 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:37:38 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:37:38 nicky-laptop kernel: [   44.002624] wlan0: authenticate with AP 00:11:95:2d:e0:30
Mar 19 19:37:38 nicky-laptop wpa_supplicant[862]: WPS-AP-AVAILABLE 
Mar 19 19:37:38 nicky-laptop wpa_supplicant[862]: Trying to associate with 00:11:95:2d:e0:30 (SSID='nicky' freq=2437 MHz)
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 19 19:37:38 nicky-laptop kernel: [   44.005415] wlan0: authenticated
Mar 19 19:37:38 nicky-laptop kernel: [   44.005432] wlan0: associate with AP 00:11:95:2d:e0:30
Mar 19 19:37:38 nicky-laptop wpa_supplicant[862]: Associated with 00:11:95:2d:e0:30
Mar 19 19:37:38 nicky-laptop kernel: [   44.009948] wlan0: RX AssocResp from 00:11:95:2d:e0:30 (capab=0x431 status=0 aid=3)
Mar 19 19:37:38 nicky-laptop kernel: [   44.009965] wlan0: associated
Mar 19 19:37:38 nicky-laptop kernel: [   44.011541] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 19 19:37:38 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-CONNECTED - Connection to 00:11:95:2d:e0:30 completed (auth) [id=0 id_str=]
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'nicky'.
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  dhclient started with pid 1641
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 19 19:37:38 nicky-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 19 19:37:38 nicky-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 19 19:37:38 nicky-laptop dhclient: All rights reserved.
Mar 19 19:37:38 nicky-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 19 19:37:38 nicky-laptop dhclient: 
Mar 19 19:37:38 nicky-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Mar 19 19:37:38 nicky-laptop dhclient: Listening on LPF/wlan0/90:4c:e5:67:ae:e2
Mar 19 19:37:38 nicky-laptop dhclient: Sending on   LPF/wlan0/90:4c:e5:67:ae:e2
Mar 19 19:37:38 nicky-laptop dhclient: Sending on   Socket/fallback
Mar 19 19:37:39 nicky-laptop avahi-daemon[762]: Registering new address record for fe80::924c:e5ff:fe67:aee2 on wlan0.*.
Mar 19 19:37:42 nicky-laptop dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
Mar 19 19:37:42 nicky-laptop dhclient: DHCPACK of 192.168.0.101 from 192.168.0.1
Mar 19 19:37:42 nicky-laptop dhclient: bound to 192.168.0.101 -- renewal in 285056 seconds.
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>    address 192.168.0.101
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>    gateway 192.168.0.1
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>    nameserver '64.71.255.198'
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>    domain name 'phub.net.cable.rogers.com'
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 19 19:37:42 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 19 19:37:42 nicky-laptop avahi-daemon[762]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Mar 19 19:37:42 nicky-laptop avahi-daemon[762]: New relevant interface wlan0.IPv4 for mDNS.
Mar 19 19:37:42 nicky-laptop avahi-daemon[762]: Registering new address record for 192.168.0.101 on wlan0.IPv4.
Mar 19 19:37:43 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Mar 19 19:37:43 nicky-laptop NetworkManager: <info>  Policy set 'Auto nicky' (wlan0) as default for routing and DNS.
Mar 19 19:37:43 nicky-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Mar 19 19:37:43 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 19 19:37:44 nicky-laptop ntpdate[1699]: adjust time server 91.189.94.4 offset 0.124531 sec
Mar 19 19:37:48 nicky-laptop kernel: [   54.540120] wlan0: no IPv6 routers present
Mar 19 19:38:02 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:38:42 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:38:46 nicky-laptop kernel: [  111.940089] CE: hpet increasing min_delta_ns to 15000 nsec
Mar 19 19:39:42 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:40:14 nicky-laptop kernel: [  199.987774] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Mar 19 19:41:02 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:42:42 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:44:42 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:45:30 nicky-laptop kernel: [  515.996116] wlan0: no probe response from AP 00:11:95:2d:e0:30 - disassociating
Mar 19 19:45:30 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 19 19:45:30 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Mar 19 19:45:30 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:45:31 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:45:31 nicky-laptop wpa_supplicant[862]: Trying to associate with 00:11:95:2d:e0:30 (SSID='nicky' freq=2437 MHz)
Mar 19 19:45:31 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 19 19:45:31 nicky-laptop kernel: [  516.781432] wlan0: authenticate with AP 00:11:95:2d:e0:30
Mar 19 19:45:31 nicky-laptop kernel: [  516.788198] wlan0: authenticated
Mar 19 19:45:31 nicky-laptop kernel: [  516.788216] wlan0: associate with AP 00:11:95:2d:e0:30
Mar 19 19:45:31 nicky-laptop kernel: [  516.791371] wlan0: RX ReassocResp from 00:11:95:2d:e0:30 (capab=0x431 status=0 aid=3)
Mar 19 19:45:31 nicky-laptop kernel: [  516.791388] wlan0: associated
Mar 19 19:45:31 nicky-laptop wpa_supplicant[862]: Associated with 00:11:95:2d:e0:30
Mar 19 19:45:31 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-CONNECTED - Connection to 00:11:95:2d:e0:30 completed (reauth) [id=0 id_str=]
Mar 19 19:45:31 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 19 19:45:31 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 19 19:45:40 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 19 19:45:40 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Mar 19 19:45:40 nicky-laptop kernel: [  526.000161] wlan0: no probe response from AP 00:11:95:2d:e0:30 - disassociating
Mar 19 19:45:40 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:45:41 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:45:41 nicky-laptop wpa_supplicant[862]: Trying to associate with 00:11:95:2d:e0:30 (SSID='nicky' freq=2437 MHz)
Mar 19 19:45:41 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 19 19:45:41 nicky-laptop kernel: [  526.789440] wlan0: authenticate with AP 00:11:95:2d:e0:30
Mar 19 19:45:41 nicky-laptop kernel: [  526.823372] wlan0: authenticated
Mar 19 19:45:41 nicky-laptop kernel: [  526.823390] wlan0: associate with AP 00:11:95:2d:e0:30
Mar 19 19:45:41 nicky-laptop wpa_supplicant[862]: Associated with 00:11:95:2d:e0:30
Mar 19 19:45:41 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-CONNECTED - Connection to 00:11:95:2d:e0:30 completed (reauth) [id=0 id_str=]
Mar 19 19:45:41 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 19 19:45:41 nicky-laptop kernel: [  526.838928] wlan0: RX ReassocResp from 00:11:95:2d:e0:30 (capab=0x431 status=0 aid=3)
Mar 19 19:45:41 nicky-laptop kernel: [  526.838942] wlan0: associated
Mar 19 19:45:41 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 19 19:46:07 nicky-laptop kernel: [  553.004176] wlan0: no probe response from AP 00:11:95:2d:e0:30 - disassociating
Mar 19 19:46:07 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 19 19:46:07 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Mar 19 19:46:07 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:46:08 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:08 nicky-laptop wpa_supplicant[862]: WPS-AP-AVAILABLE 
Mar 19 19:46:08 nicky-laptop wpa_supplicant[862]: Trying to associate with 00:11:95:2d:e0:30 (SSID='nicky' freq=2437 MHz)
Mar 19 19:46:08 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 19 19:46:08 nicky-laptop kernel: [  553.781608] wlan0: authenticate with AP 00:11:95:2d:e0:30
Mar 19 19:46:08 nicky-laptop kernel: [  553.801623] wlan0: authenticated
Mar 19 19:46:08 nicky-laptop wpa_supplicant[862]: Associated with 00:11:95:2d:e0:30
Mar 19 19:46:08 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-CONNECTED - Connection to 00:11:95:2d:e0:30 completed (reauth) [id=0 id_str=]
Mar 19 19:46:08 nicky-laptop kernel: [  553.801635] wlan0: associate with AP 00:11:95:2d:e0:30
Mar 19 19:46:08 nicky-laptop kernel: [  553.804584] wlan0: RX ReassocResp from 00:11:95:2d:e0:30 (capab=0x431 status=0 aid=3)
Mar 19 19:46:08 nicky-laptop kernel: [  553.804595] wlan0: associated
Mar 19 19:46:08 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 19 19:46:08 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 19 19:46:20 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 19 19:46:20 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Mar 19 19:46:20 nicky-laptop kernel: [  566.012134] wlan0: no probe response from AP 00:11:95:2d:e0:30 - disassociating
Mar 19 19:46:20 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:46:21 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:26 nicky-laptop kernel: [  571.999396] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:27 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:32 nicky-laptop kernel: [  577.824735] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:32 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1641
Mar 19 19:46:36 nicky-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto nicky'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 19 19:46:36 nicky-laptop avahi-daemon[762]: Withdrawing address record for 192.168.0.101 on wlan0.
Mar 19 19:46:36 nicky-laptop avahi-daemon[762]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Mar 19 19:46:36 nicky-laptop avahi-daemon[762]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto nicky' has security, but secrets are required.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto nicky' has security, and secrets exist.  No new secrets needed.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'ssid' value 'nicky'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Mar 19 19:46:36 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 19:46:36 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 19 19:46:36 nicky-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 19 19:46:37 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 19:46:38 nicky-laptop kernel: [  583.657321] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:38 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:43 nicky-laptop kernel: [  589.493144] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:44 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:49 nicky-laptop kernel: [  595.320540] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:50 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:46:55 nicky-laptop kernel: [  601.156602] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:46:56 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:47:01 nicky-laptop kernel: [  606.985083] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:47:02 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:47:07 nicky-laptop kernel: [  612.852703] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:47:08 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:47:13 nicky-laptop kernel: [  618.711040] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:47:13 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:47:18 nicky-laptop kernel: [  624.569002] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:47:19 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:47:24 nicky-laptop kernel: [  630.412954] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 19:47:25 nicky-laptop wpa_supplicant[862]: CTRL-EVENT-SCAN-RESULTS 
-------------------------------------------------------------

Someone please help me :(

---

### Post by serious7 on 2010-03-19
This time it failed but it reconected. It didnt require a reboot this time. its getting really annoying.
----------------------------------------
r 19 19:49:44 nicky-laptop kernel: [   54.572099] wlan0: no IPv6 routers present
Mar 19 19:49:58 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:50:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:51:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:52:58 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:54:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:56:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 19:58:31 nicky-laptop kernel: [  581.416120] CE: hpet increasing min_delta_ns to 15000 nsec
Mar 19 19:58:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:00:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:02:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:22 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 19 20:03:22 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Mar 19 20:03:22 nicky-laptop kernel: [  871.988178] wlan0: no probe response from AP 00:11:95:2d:e0:30 - disassociating
Mar 19 20:03:22 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 20:03:22 nicky-laptop kernel: [  872.128546] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:23 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:28 nicky-laptop kernel: [  877.956536] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:29 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:34 nicky-laptop kernel: [  883.789012] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:34 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1657
Mar 19 20:03:38 nicky-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Mar 19 20:03:38 nicky-laptop avahi-daemon[760]: Withdrawing address record for 192.168.0.101 on wlan0.
Mar 19 20:03:38 nicky-laptop avahi-daemon[760]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Mar 19 20:03:38 nicky-laptop avahi-daemon[760]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto nicky'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto nicky' has security, but secrets are required.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto nicky' has security, and secrets exist.  No new secrets needed.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'ssid' value 'nicky'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Mar 19 20:03:38 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 20:03:38 nicky-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 19 20:03:38 nicky-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 19 20:03:39 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 19 20:03:39 nicky-laptop kernel: [  889.612582] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:40 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:45 nicky-laptop kernel: [  895.446634] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:46 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:51 nicky-laptop kernel: [  901.272536] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Mar 19 20:03:52 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:58 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:03:58 nicky-laptop wpa_supplicant[867]: Trying to associate with 00:11:95:2d:e0:30 (SSID='nicky' freq=2437 MHz)
Mar 19 20:03:58 nicky-laptop kernel: [  907.713790] wlan0: authenticate with AP 00:11:95:2d:e0:30
Mar 19 20:03:58 nicky-laptop kernel: [  907.715836] wlan0: authenticated
Mar 19 20:03:58 nicky-laptop kernel: [  907.715854] wlan0: associate with AP 00:11:95:2d:e0:30
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 19 20:03:58 nicky-laptop wpa_supplicant[867]: Associated with 00:11:95:2d:e0:30
Mar 19 20:03:58 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-CONNECTED - Connection to 00:11:95:2d:e0:30 completed (reauth) [id=0 id_str=]
Mar 19 20:03:58 nicky-laptop kernel: [  907.718885] wlan0: RX ReassocResp from 00:11:95:2d:e0:30 (capab=0x431 status=0 aid=3)
Mar 19 20:03:58 nicky-laptop kernel: [  907.718904] wlan0: associated
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'nicky'.
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 19 20:03:58 nicky-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 19 20:03:58 nicky-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 19 20:03:58 nicky-laptop dhclient: All rights reserved.
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  dhclient started with pid 1982
Mar 19 20:03:58 nicky-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 19 20:03:58 nicky-laptop dhclient: 
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 19 20:03:58 nicky-laptop dhclient: Listening on LPF/wlan0/90:4c:e5:67:ae:e2
Mar 19 20:03:58 nicky-laptop dhclient: Sending on   LPF/wlan0/90:4c:e5:67:ae:e2
Mar 19 20:03:58 nicky-laptop dhclient: Sending on   Socket/fallback
Mar 19 20:03:58 nicky-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Mar 19 20:04:00 nicky-laptop dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
Mar 19 20:04:00 nicky-laptop dhclient: DHCPACK of 192.168.0.101 from 192.168.0.1
Mar 19 20:04:00 nicky-laptop dhclient: bound to 192.168.0.101 -- renewal in 233010 seconds.
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>    address 192.168.0.101
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>    gateway 192.168.0.1
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>    nameserver '64.71.255.198'
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>    domain name 'phub.net.cable.rogers.com'
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 19 20:04:00 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 19 20:04:00 nicky-laptop avahi-daemon[760]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Mar 19 20:04:00 nicky-laptop avahi-daemon[760]: New relevant interface wlan0.IPv4 for mDNS.
Mar 19 20:04:00 nicky-laptop avahi-daemon[760]: Registering new address record for 192.168.0.101 on wlan0.IPv4.
Mar 19 20:04:01 nicky-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Mar 19 20:04:01 nicky-laptop NetworkManager: <info>  Policy set 'Auto nicky' (wlan0) as default for routing and DNS.
Mar 19 20:04:01 nicky-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Mar 19 20:04:01 nicky-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 19 20:04:02 nicky-laptop ntpdate[2042]: adjust time server 91.189.94.4 offset 0.019931 sec
Mar 19 20:04:38 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 20:05:18 nicky-laptop wpa_supplicant[867]: CTRL-EVENT-SCAN-RESULTS 
-------------------------------------------------

---

### Post by Chronon on 2010-03-19
It seems there is a regression in wifi support in the kernel.  I think this is supposed to be improved a bit in newer versions of the kernel.  However, I installed the latest stable compat-wireless drivers and still can't get online with it.  

I think things were working fine in 9.04, so maybe it's best to go back to an older version until this problem is sorted.  Or, you can probably install windows drivers with ndiswrapper until a kernel with better support makes it into the repositories.

BTW: I have a wireless card with Atheros AR928X chipset.

---

### Post by serious7 on 2010-03-20
I use ubuntu netbook remix. Does someone else have a different opinion on this or am I out of luck?

---

### Post by bri5569 on 2010-03-21
I used to have the same problems but since installing WICD (another network manager) I have never had a crash or have to re-connect. I am not an experienced Linux user but after finding WICD to be an outstanding network manager I have completely removed windows from my computer. You can find WICD in Ubuntu software Centre.

---

