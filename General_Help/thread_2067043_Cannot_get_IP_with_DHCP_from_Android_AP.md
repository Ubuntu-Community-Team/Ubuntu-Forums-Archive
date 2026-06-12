---
title: "Cannot get IP with DHCP from Android AP"
date: 2012-10-06
forum: General Help
---

### Post by mercmobily on 2012-10-06
Hi,

I am having a problem with my Ubuntu 12.4. Basically, while I can connect fine with a "normal" wireless access point, I am having great difficulty connecting to anything else -- neither with my Android Phone withing as an AP (stock Android 4.0.4 kernel 3.0.8) and with a tiny Telstra access point.

I am actually in hospital looking after my wife who just had an emergency C section, so spending time tinkering with things is a little complicated -- help!

Here is the log of what happens. From what I understand, authentication goes through but then the DHCP client fails to obtain an IP address. Both the Telstra AP and the Android phone used to work. I tried using another computer, again with Ubuntu 12.4 (the one my wife is meant to use in hospital!), but nothing.

Can somebody please help? Here is the log:

```
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): disconnecting for new activation request.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): device state change: ip-config -> disconnected (reason 'none') [70 30 0]
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): deactivating device (reason 'none') [0]
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 3237
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: Withdrawing address record for fe80::e294:67ff:fe0a:a440 on wlan1.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::e294:67ff:fe0a:a440.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: Interface wlan1.IPv6 no longer relevant for mDNS.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.014432] wlan1: deauthenticating from 98:f5:37:9f:6e:be by local choice (reason=3)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.087037] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.087051] cfg80211: Restoring regulatory settings
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.087063] cfg80211: Calling CRDA to update world regulatory domain
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) starting connection 'TTHS_A93F38'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1/wireless): connection 'TTHS_A93F38' has security, and secrets exist.  No new secrets needed.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'ssid' value 'TTHS_A93F38'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'scan_ssid' value '1'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'key_mgmt' value 'NONE'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'auth_alg' value 'OPEN'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'wep_key0' value '<omitted>'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'wep_key1' value '<omitted>'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: added 'wep_tx_keyidx' value '0'
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: completed -> disconnected
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118041] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118045] cfg80211: World regulatory domain updated:
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118046] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118049] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118052] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118054] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118056] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 kernel: [  799.118058] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Config: set interface ap_scan to 1
Oct  6 12:13:36 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to authenticate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to associate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.362281] wlan1: authenticate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.364917] wlan1: authenticated
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.365766] wlan1: associate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.368037] wlan1: RX ReassocResp from 98:f5:37:9f:6e:be (capab=0x431 status=0 aid=1)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.368046] wlan1: associated
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: authenticating -> associating
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Associated with 98:f5:37:9f:6e:be
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-CONNECTED - Connection to 98:f5:37:9f:6e:be completed (reauth) [id=0 id_str=]
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.371238] cfg80211: Calling CRDA for country: US
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: associating -> completed
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TTHS_A93F38'.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382362] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382377] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382386] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382396] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382404] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382413] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382421] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382430] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382437] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382446] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382462] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382469] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382478] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382485] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382494] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382502] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382518] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382528] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382535] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382544] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382551] cfg80211: Disabling freq 2467 MHz
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382556] cfg80211: Disabling freq 2472 MHz
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382566] cfg80211: Regulatory domain changed to country: US
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382572] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382581] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382590] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382598] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382608] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382616] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 kernel: [  799.382625] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> dhclient started with pid 3391
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Beginning IP6 addrconf.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: All rights reserved.
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: 
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: Listening on LPF/wlan1/e0:94:67:0a:a4:40
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: Sending on   LPF/wlan1/e0:94:67:0a:a4:40
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: Sending on   Socket/fallback
Oct  6 12:13:37 daniela-ThinkPad-Edge-E320 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Oct  6 12:13:38 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::e294:67ff:fe0a:a440.
Oct  6 12:13:38 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: New relevant interface wlan1.IPv6 for mDNS.
Oct  6 12:13:38 daniela-ThinkPad-Edge-E320 avahi-daemon[1115]: Registering new address record for fe80::e294:67ff:fe0a:a440 on wlan1.*.
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.848658] wlan1: disassociated from 98:f5:37:9f:6e:be (Reason: 2)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-DISCONNECTED bssid=98:f5:37:9f:6e:be reason=2
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=2
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.934841] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.934846] cfg80211: Restoring regulatory settings
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.934859] cfg80211: Calling CRDA to update world regulatory domain
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938078] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938081] cfg80211: World regulatory domain updated:
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938082] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938085] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938087] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938089] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938091] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 kernel: [  801.938092] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: completed -> disconnected
Oct  6 12:13:39 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to authenticate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.276492] wlan1: authenticate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to associate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.279381] wlan1: authenticated
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.279945] wlan1: associate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.282143] wlan1: RX ReassocResp from 98:f5:37:9f:6e:be (capab=0x431 status=0 aid=1)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.282153] wlan1: associated
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Associated with 98:f5:37:9f:6e:be
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: authenticating -> associating
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.285551] cfg80211: Calling CRDA for country: US
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-CONNECTED - Connection to 98:f5:37:9f:6e:be completed (reauth) [id=0 id_str=]
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: associating -> completed
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298194] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298201] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298204] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298207] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298210] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298214] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298216] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298219] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298264] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298268] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298271] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298274] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298277] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298283] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298286] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298289] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298292] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298296] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298304] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298310] cfg80211: Disabling freq 2467 MHz
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298312] cfg80211: Disabling freq 2472 MHz
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298317] cfg80211: Regulatory domain changed to country: US
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298321] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298324] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298327] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298330] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298333] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298335] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 kernel: [  802.298338] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Oct  6 12:13:40 daniela-ThinkPad-Edge-E320 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
Oct  6 12:13:46 daniela-ThinkPad-Edge-E320 kernel: [  809.177617] wlan1: disassociated from 98:f5:37:9f:6e:be (Reason: 2)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-DISCONNECTED bssid=98:f5:37:9f:6e:be reason=2
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=2
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.278228] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.278245] cfg80211: Restoring regulatory settings
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.278255] cfg80211: Calling CRDA to update world regulatory domain
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: completed -> disconnected
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287509] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287519] cfg80211: World regulatory domain updated:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287523] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287531] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287537] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287543] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287549] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.287555] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to authenticate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.594735] wlan1: authenticate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Trying to associate with 98:f5:37:9f:6e:be (SSID='TTHS_A93F38' freq=2422 MHz)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.596993] wlan1: authenticated
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.597269] wlan1: associate with 98:f5:37:9f:6e:be (try 1)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.599440] wlan1: RX ReassocResp from 98:f5:37:9f:6e:be (capab=0x431 status=0 aid=1)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.599444] wlan1: associated
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: Associated with 98:f5:37:9f:6e:be
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 wpa_supplicant[1304]: CTRL-EVENT-CONNECTED - Connection to 98:f5:37:9f:6e:be completed (reauth) [id=0 id_str=]
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): supplicant interface state: authenticating -> completed
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.601962] cfg80211: Calling CRDA for country: US
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605179] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605182] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605183] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605185] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605187] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605188] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605190] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605193] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605194] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605196] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605198] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605199] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605201] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605212] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605213] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605215] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605217] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605218] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605220] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605222] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605223] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605225] cfg80211: Disabling freq 2467 MHz
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605226] cfg80211: Disabling freq 2472 MHz
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605228] cfg80211: Regulatory domain changed to country: US
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605229] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605231] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605232] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605234] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605236] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605247] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  809.605248] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
Oct  6 12:13:47 daniela-ThinkPad-Edge-E320 kernel: [  810.172087] wlan1: no IPv6 routers present
Oct  6 12:13:57 daniela-ThinkPad-Edge-E320 NetworkManager[1093]: <info> (wlan1): IP6 addrconf timed out or failed.
```

Thanks a million!

Merc.

---

### Post by mercmobily on 2012-10-06
(Subscribed)

(This is us :D )

---

### Post by mercmobily on 2012-10-06
This is what happens if I try to run dhclient manually while teh connection is being established (so wlan1 is there)...


```
$ sudo dhclient -v wlan1
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan1/e0:94:67:0a:a4:40
Sending on   LPF/wlan1/e0:94:67:0a:a4:40
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
```

---

