---
title: "Frequent (random intervals)  wireless router disconnects"
date: 2011-06-20
forum: General Help
---

### Post by prem1er on 2011-06-20
Hi, 
  I'm having issue with my wireless connection. I'm not sure if it is the WPA security causing the issue, but I randomly lose connection to the router. The network manager then scans for available wireless routers for a bit before trying to reconnect to my router and asking for my wireless password again. Here is the log from the start of the disconnect to when it is reconnected.

```

Jun 18 10:34:53 lahey kernel: [ 1500.288923] dumpcap uses obsolete (PF_INET,SOCK_PACKET)
Jun 18 10:43:36 lahey wpa_supplicant[1059]: CTRL-EVENT-DISCONNECTED bssid=00:25:9c:48:41:ff reason=0
Jun 18 10:43:36 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Jun 18 10:43:36 lahey kernel: [ 2023.153690] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 18 10:43:36 lahey kernel: [ 2023.153700] cfg80211: Restoring regulatory settings
Jun 18 10:43:36 lahey kernel: [ 2023.153710] cfg80211: Calling CRDA to update world regulatory domain
Jun 18 10:43:36 lahey kernel: [ 2023.162762] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun 18 10:43:36 lahey kernel: [ 2023.162776] cfg80211: World regulatory domain updated:
Jun 18 10:43:36 lahey kernel: [ 2023.162780] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 18 10:43:36 lahey kernel: [ 2023.162788] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 18 10:43:36 lahey kernel: [ 2023.162796] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 18 10:43:36 lahey kernel: [ 2023.162802] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 18 10:43:36 lahey kernel: [ 2023.162809] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 18 10:43:36 lahey kernel: [ 2023.162816] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 18 10:43:36 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 8 -> 3 (reason 11)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): deactivating device (reason: 11).
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1813
Jun 18 10:43:51 lahey avahi-daemon[935]: Withdrawing address record for 192.168.1.102 on wlan0.
Jun 18 10:43:51 lahey avahi-daemon[935]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.102.
Jun 18 10:43:51 lahey avahi-daemon[935]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) starting connection 'Auto test'
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0/wireless): access point 'Auto test' has security, but secrets are required.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 10:43:51 lahey NetworkManager[950]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0/wireless): connection 'Auto test' has security, and secrets exist.  No new secrets needed.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Config: added 'ssid' value 'test'
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Config: added 'scan_ssid' value '1'
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Config: added 'psk' value '<omitted>'
Jun 18 10:43:51 lahey NetworkManager[950]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 18 10:43:51 lahey NetworkManager[950]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 18 10:43:51 lahey NetworkManager[950]: <info> Config: set interface ap_scan to 1
Jun 18 10:43:55 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 18 10:44:52 lahey NetworkManager[950]: <warn> Activation (wlan0/wireless): association took too long.
Jun 18 10:44:52 lahey NetworkManager[950]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun 18 10:44:52 lahey NetworkManager[950]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun 18 10:44:52 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 10:44:54 lahey NetworkManager[950]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 10:44:54 lahey NetworkManager[950]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0/wireless): connection 'Auto test' has security, and secrets exist.  No new secrets needed.
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Config: added 'ssid' value 'test'
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Config: added 'scan_ssid' value '1'
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Config: added 'psk' value '<omitted>'
Jun 18 10:44:54 lahey NetworkManager[950]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 18 10:44:54 lahey NetworkManager[950]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 18 10:44:54 lahey NetworkManager[950]: <info> Config: set interface ap_scan to 1
Jun 18 10:44:57 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 18 10:45:04 lahey wpa_supplicant[1059]: Trying to associate with 00:25:9c:48:xx:xx (SSID='test' freq=2417 MHz)
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 18 10:45:04 lahey kernel: [ 2110.933574] wlan0: authenticate with 00:25:9c:48:xx:xx (try 1)
Jun 18 10:45:04 lahey wpa_supplicant[1059]: Associated with 00:25:9c:48:xx:xx
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  associating -> associated
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun 18 10:45:04 lahey kernel: [ 2110.950079] wlan0: authenticated
Jun 18 10:45:04 lahey kernel: [ 2110.950128] wlan0: associate with 00:25:9c:48:xx:xx (try 1)
Jun 18 10:45:04 lahey kernel: [ 2110.952905] wlan0: RX AssocResp from 00:25:9c:48:xx:xx (capab=0x411 status=0 aid=3)
Jun 18 10:45:04 lahey kernel: [ 2110.952913] wlan0: associated
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun 18 10:45:04 lahey wpa_supplicant[1059]: WPA: Key negotiation completed with 00:25:9c:48:xx:xx [PTK=TKIP GTK=TKIP]
Jun 18 10:45:04 lahey wpa_supplicant[1059]: CTRL-EVENT-CONNECTED - Connection to 00:25:9c:48:xx:xx completed (reauth) [id=0 id_str=]
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'test'.
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 18 10:45:04 lahey NetworkManager[950]: <info> dhclient started with pid 2443
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 18 10:45:04 lahey dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jun 18 10:45:04 lahey dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jun 18 10:45:04 lahey dhclient: All rights reserved.
Jun 18 10:45:04 lahey dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 18 10:45:04 lahey dhclient: 
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 18 10:45:04 lahey dhclient: Listening on LPF/wlan0/00:15:af:dd:xx:xx
Jun 18 10:45:04 lahey dhclient: Sending on   LPF/wlan0/00:15:af:dd:xx:xx
Jun 18 10:45:04 lahey dhclient: Sending on   Socket/fallback
Jun 18 10:45:04 lahey dhclient: DHCPREQUEST of 192.168.1.102 on wlan0 to 255.255.255.255 port 67
Jun 18 10:45:04 lahey dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Jun 18 10:45:04 lahey NetworkManager[950]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   address 192.168.1.102
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   prefix 24 (255.255.255.0)
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   gateway 192.168.1.1
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   nameserver '192.168.1.1'
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   nameserver '68.87.64.xxx'
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   nameserver '68.87.75.xxx'
Jun 18 10:45:04 lahey NetworkManager[950]: <info>   domain name 'hsd1.xxxx.'
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Scheduling stage 5
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Done scheduling stage 5
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 18 10:45:04 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun 18 10:45:04 lahey avahi-daemon[935]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.102.
Jun 18 10:45:04 lahey dhclient: bound to 192.168.1.102 -- renewal in 42064 seconds.
Jun 18 10:45:04 lahey avahi-daemon[935]: New relevant interface wlan0.IPv4 for mDNS.
Jun 18 10:45:04 lahey avahi-daemon[935]: Registering new address record for 192.168.1.102 on wlan0.IPv4.
Jun 18 10:45:05 lahey NetworkManager[950]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Jun 18 10:45:05 lahey NetworkManager[950]: <info> Policy set 'Auto test' (wlan0) as default for IPv4 routing and DNS.
Jun 18 10:45:05 lahey NetworkManager[950]: <info> Activation (wlan0) successful, device activated.
Jun 18 10:45:05 lahey NetworkManager[950]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 18 10:45:13 lahey ntpdate[2490]: adjust time server 91.189.94.4 offset 0.064103 sec

```

TIA

---

