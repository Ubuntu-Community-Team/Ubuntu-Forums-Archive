---
title: "Wireless Problems | Do I need firmware, ndiswrapper, or other?"
date: 2006-06-05
forum: General Help
---

### Post by bieber on 2006-06-05
Hello, all.  I currently have two computers, one of which has a wired connection, which I am currently running Ubuntu Dapper on with no problems (it's the computer I'm typing this on), and one which has no way to connect to the internet other than by way of a LInksys WUSB54G wireless adapter.  On that computer, I currently run SuSE 10.0, and get wireless using ndiswrapper.  I'm trying to get wireless working in Ubuntu on that computer, but as of yet, I haven't had any luck.

Ubuntu detected the wireless card immediately, but I couldn't get it to connect to my network.  Later on, I saw a tutorial on this forum for getting firmware for Broadcom cards, and installing Network Manager.  So, I dragged it out to my living room, got a temporary wired connection, and installed Network Manager and the Broadcom firmware cutter.  The firmware cutter refused to work on the drivers for my wireless adapter, so I tried them on the drivers linked to in the tutorial, and then went back to try and connect wirelessly.

Now, network manager acknowledges that I have a wireless adapter, but it says that there are no wireless networks in range, even though mine should be visible.  I tried typing in the SSID and WEP key of my network (copied and pasted from the output of ifstatus on the SuSE partition, so I know there were no typos) and, after a somewhat lengthy delay, it failed to connect.

So, does anyone know what I need to do?  Is there some way to get firmware for my Linksys adapter like they did for Broadcom cards in the tutorial?  If not, how do I go about getting ndiswrapper to work on Ubuntu and configure things from network manager?  Is there a decent tutorial somewhere for either?

Thank you,
Robert Bieber

---

### Post by nadeldave on 2006-06-05
I like to tail -f /var/log/syslog when I try to connect to wireless networks and am having trouble.
If you see a bunch of DHCP requests, you know the router is trying to access the network and failing.  If it doesn't get that far, you can be sure its a driver problem or a configuration error.
Don't know if that helps, but it may shed some light.

---

### Post by bieber on 2006-06-07
Well, I'm not sure why, but I booted into Ubuntu to try that, and suddenly Network Manager showed all the networks in my area.  However, it still failed when I typed in my WEP key and tried to connect to mine.  Here's what tail gave me during the attempt.
```

Jun  7 15:46:29 bieber-desktop NetworkManager: <information>^Imatch
Jun  7 15:46:29 bieber-desktop NetworkManager: <debug info>^I[1149709589.164233] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'COUPLANDPORTERFAMILYNETWORK'
Jun  7 15:46:29 bieber-desktop NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth2 / COUPLANDPORTERFAMILYNETWORK
Jun  7 15:46:29 bieber-desktop NetworkManager: <information>^IDeactivating device eth2.
Jun  7 15:46:31 bieber-desktop NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_wep_enc_key (): error setting key for device eth2: Unknown error 524
Jun  7 15:46:31 bieber-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IDevice eth2 activation scheduled...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) started...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting...
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2/wireless): access point 'COUPLANDPORTERFAMILYNETWORK' is encrypted, but NO valid key exists.  New key needed.
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) New wireless user key requested for network 'COUPLANDPORTERFAMILYNETWORK'.
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete.
Jun  7 15:46:31 bieber-desktop NetworkManager: <information>^Imatch
Jun  7 15:46:31 bieber-desktop last message repeated 11 times
Jun  7 15:46:34 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
Jun  7 15:46:37 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
Jun  7 15:46:42 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
Jun  7 15:46:49 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) New wireless user key for network 'COUPLANDPORTERFAMILYNETWORK' received.
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) started...
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) starting...
Jun  7 15:46:49 bieber-desktop NetworkManager: <information>^IActivation (eth2/wireless): access point 'COUPLANDPORTERFAMILYNETWORK' is encrypted, and a key exists.  No new key needed.
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth2^I^Iwext^I/var/run/wpa_supplicant^I'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was '0'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 434f55504c414e44504f5254455246414d494c594e4554574f524b'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_key0 <key>'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^ISUP: response was 'OK'
Jun  7 15:46:50 bieber-desktop NetworkManager: <information>^IActivation (eth2) Stage 2 of 5 (Device Configure) complete.
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Global control interface '/var/run/wpa_supplicant-global'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX global ctrl_iface - hexdump_ascii(len=49):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      68 32 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h2__wext_/var/ru
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      09                                                _
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth2^I^Iwext^I/var/run/wpa_supplicant^I'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Initializing interface 'eth2' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Initializing interface (2) 'eth2'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAPOL: SUPP_PAE entering state DISCONNECTED
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAPOL: SUPP_BE entering state INITIALIZE
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAP: EAP entering state DISABLED
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAPOL: External notification - portEnabled=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): EAPOL: External notification - portValid=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):   capabilities: key_mgmt 0x0 enc 0x3
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Own MAC address: 00:0c:41:d9:fe:64
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_wpa
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Driver did not support SIOCSIWENCODEEXT
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Driver did not support SIOCSIWENCODEEXT
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Driver did not support SIOCSIWENCODEEXT
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Driver did not support SIOCSIWENCODEEXT
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_countermeasures
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wpa_driver_wext_set_drop_unencrypted
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Setting scan request: 0 sec 100000 usec
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Added interface eth2
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Wireless event: cmd=0x8b06 len=8
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=9):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=11):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: ADD_NETWORK
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=73):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): 34f55504c414
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      65 34 34 35 30 34 66 35 32 35 34 34 35 35 32 34   e44504f525445524
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      36 34 31 34 64 34 39 34 63 35 39 34 65 34 35 35   6414d494c594e455
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      34 35 37 34 66 35 32 34 62                        4574f524b
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='434f55504c414e44504f5254455246414d494c594e4554574f524b'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): ssid - hexdump_ascii(len=27):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      43 4f 55 50 4c 41 4e 44 50 4f 52 54 45 52 46 41   COUPLANDPORTERFA
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      4d 49 4c 59 4e 45 54 57 4f 52 4b                  MILYNETWORK
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=27):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): key_mgmt: 0x4
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=49): [REMOVED]
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: SET_NETWORK id=0 name='wep_key0' value='[REMOVED]'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wep_key0 - hexdump(len=13): [REMOVED]
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=29):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 77 65   SET_NETWORK 0 we
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      70 5f 74 78 5f 6b 65 79 69 64 78 20 30            p_tx_keyidx 0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: SET_NETWORK id=0 name='wep_tx_keyidx' value='0'
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): wep_tx_keyidx=0 (0x0)
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=16):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE: ENABLE_NETWORK id=0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Setting scan request: 0 sec 0 usec
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): State: DISCONNECTED -> SCANNING
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Starting AP scan (broadcast SSID)
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): RX ctrl_iface - hexdump_ascii(len=6):
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717):      41 54 54 41 43 48                                 ATTACH
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): CTRL_IFACE monitor attached - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 35 35 2d 35 00 00 00
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Scan timeout - try to get results
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Received 0 bytes of scan results (0 BSSes)
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Scan results: 0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Selecting BSS from priority group 0
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): No suitable AP found.
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Setting scan request: 5 sec 0 usec
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Starting AP scan (broadcast SSID)
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Scan timeout - try to get results
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Received 0 bytes of scan results (0 BSSes)
Jun  7 15:47:01 bieber-desktop NetworkManager: <information>^Iwpa_supplicant(5717): Scan results: 0
Jun  7 15:47:03 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
Jun  7 15:47:15 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 18
Jun  7 15:47:33 bieber-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
Jun  7 15:47:35 bieber-desktop dhclient: No DHCPOFFERS received.
Jun  7 15:47:35 bieber-desktop dhclient: No working leases in persistent database - sleeping.
Jun  7 15:47:50 bieber-desktop NetworkManager: <information>^IActivation (eth2/wireless): association took too long (>60s), failing activation.
Jun  7 15:47:50 bieber-desktop NetworkManager: <information>^IActivation (eth2) failure scheduled...
Jun  7 15:47:50 bieber-desktop NetworkManager: <information>^IActivation (eth2) failed for access point (COUPLANDPORTERFAMILYNETWORK)
Jun  7 15:47:50 bieber-desktop NetworkManager: <information>^IActivation (eth2) failed.
Jun  7 15:47:50 bieber-desktop NetworkManager: <information>^IDeactivating device eth2.
Jun  7 15:47:50 bieber-desktop dhclient: receive_packet failed on eth2: Network is down
Jun  7 15:47:52 bieber-desktop NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_wep_enc_key (): error setting key for device eth2: Unknown error 524
Jun  7 15:47:52 bieber-desktop NetworkManager: <information>^Imatch
Jun  7 15:48:00 bieber-desktop kernel: [4295160.493000] ADDRCONF(NETDEV_UP): eth2: link is not ready

```

I'm afraid I don't know what it all means.  Anyone have any ideas?

---

### Post by msak007 on 2006-06-07
Is your network encrypted using WPA? I see a bunch of wpa_supplicant lines in there, so maybe that's not configured right? Also, I've had some issues where when I try to connect the Network Manager prompts me for my key, gets to Stage 2 (of 5), then hangs for a couple minutes before dying and not connecting. I'm not sure if you've tried this but when that's happened to me usually a router reboot fixes it for some reason.

---

### Post by bionnaki on 2006-06-07
not the same card, but maybe try this: [http://www.ubuntuforums.org/showthread.php?t=161376](http://www.ubuntuforums.org/showthread.php?t=161376)

they might use the same chipset
and if so
then it should work.

---

### Post by bieber on 2006-06-07
It's definitely WEP, not WPA, and I'm pretty sure it's not a router problem, because I'm currently using the adapter in SuSE with ndiswrapper.  I'll boot into Ubuntu and see if a router reset helps, though.

---

### Post by msak007 on 2006-06-07
I decided against using the built-in bcm43xx driver w/ fwcutter because it's only limited to 11mbps, so I used ndiswrapper instead. For some reason ndiswrapper on its own wouldn't connect, but it's worked flawlessly (so far) combined with Network Manager (aside from the above-mentioned connection issues with the router). You've used ndiswrapper in SuSE so obviously you have some experience setting it up, so if fwcutter doesn't cut it (no pun intended :D) give ndiswrapper a try.

---

### Post by bieber on 2006-06-10
I just installed the Windows drivers with ndiswrapper, but on SuSE, I was able to configure wlan0 using YaST, something that I obviously can't do on Ubuntu.  How do I go about actually getting a connection with the device I've installed with ndiswrapper?  Config files?

---

### Post by msak007 on 2006-06-10
Yea I know what you mean, I set up ndiswrapper using YaST at the time. A lot of people dislike YaST, but it really made setting up a lot of things easier with the GUI. But I digress... If you want to set up ndiswrapper it's actually pretty easy using just a few commands. There's a GUI client, but it didn't work for me in Dapper for some reason. There's a lot of tutorials on ndiswrapper, but there's a few extra steps required for Dapper so I'll sum it up for you:

1. Extract the Windows drivers specific to your card somewhere easy to get to (I always use the Desktop) - make sure you get both the .sys and the .inf file.
2. Open a terminal, and navigate to the folder you extracted the drivers to.
3. Type "sudo ndiswrapper -i <name of .inf file>
4. Type "ndiswrapper -l" - if the driver installed correctly, you should see a line that has the name of the inf file you installed and next to it "driver present, hardware present". If you see this, you're almost there! If you don't, then you loaded the wrong driver. Type "ndiswrapper -e <name listed in line above after issuing ndiswrapper -l>" to remove it, and start over using a different driver.
5. Once the ndiswrapper driver is installed, you have to blacklist the built-in driver to prevent a conflict, so follow step 1.1 of [this]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e") wiki entry on how to do that. You may get an error that ndiswrapper is not loaded when you type "sudo rmmod ndiswrapper", but just in case it's already loaded I would do it anyway.
6. Type "sudo ndiswrapper -m" to make the module load at startup.
7. There's a variety of ways to restart networking, but at this point I would advise restarting the whole machine to get everything loaded.

That's it! The card will likely be detected as "ethX" instead of "wlanX". At this point if you have Network Manager installed, it should detect the card and your wireless network. Choose it, type in your key (if applicable), and you should be connected. I hope this helps.

---

### Post by bieber on 2006-06-10
WOW.  What you advised actually worked.  It gave me an error when I tried to rmmod bcm43xx (apparently it wasn't running anyways), but when I rmmod-ed and then modprobed ndiswrapper, it allowed me to connect.  The wireless interface disappeared when I rmmoded, and reappeared after modprobing.  And then I rebooted, and it doesn't work again.

The wireless card showing up in the Networking window doesn't seem to be the ndiswrapper one, because it stays there even if I rmmod ndiswrapper.  ndiswrapper itself tells me the driver is successfully installed and the hardware is present, but I'm not getting a connection.  Could there be a different module using my wireless adapter (Linksys WUSB54G) that I need to blacklist?  I'm about to try reinstalling Dapper and starting with your instructions from scratch (I may have messed something up along the way, I'm afraid).

Oh, and Network Manager stopped acknowledging the presence of a wireless adapter sometime between blacklisting the Broadcom drivers and installing the ndiswrapper drivers...

---

### Post by msak007 on 2006-06-11
Try [this]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L") (refer to #20) and [this]("http://ubuntuforums.org/showthread.php?p=1024625") to set up your card. Pretty much it seems that your card uses the Prism54 chipset / driver, not Broadcom. Try that and let me know if it works without a format.

I had a longer post but for some reason after a certain length it just hangs when I try to post. Something going on with the forums?

---

