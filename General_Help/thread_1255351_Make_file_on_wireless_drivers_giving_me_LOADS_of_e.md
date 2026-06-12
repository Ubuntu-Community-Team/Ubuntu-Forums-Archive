---
title: "Make file on wireless drivers giving me LOADS of errors... Don't know how to fix"
date: 2009-09-01
forum: General Help
---

### Post by EvenStevens on 2009-09-01
I was following [this]("http://www.ubuntugeek.com/how-to-enable-packet-injection-on-a-intel-prowireless-3945abg-wireless-card.html") tutorial and when I got to the make file, my terminal threw this mess at me

```
steve@steve-laptop:~/ipwraw-ng$ sudo make SHELL=/bin/bash
make -C /lib/modules/2.6.30-02063003-generic/build M=/home/steve/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-02063003-generic'
  CC [M]  /home/steve/ipwraw-ng/ipwraw.o
/home/steve/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or directory
In file included from /home/steve/ipwraw-ng/ipwraw.h:51,
                 from /home/steve/ipwraw-ng/ipwraw.c:48:
/home/steve/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/home/steve/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /home/steve/ipwraw-ng/ipwraw.c:48:
/home/steve/ipwraw-ng/ipwraw.h:531: error: field ‘frame’ has incomplete type
/home/steve/ipwraw-ng/ipwraw.h:532: error: ‘IEEE80211_FRAME_LEN’ undeclared here (not in a function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘frame_get_hdrlen’:
/home/steve/ipwraw-ng/ipwraw.c:52: error: ‘IEEE80211_3ADDR_LEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:52: error: (Each undeclared identifier is reported only once
/home/steve/ipwraw-ng/ipwraw.c:52: error: for each function it appears in.)
/home/steve/ipwraw-ng/ipwraw.c:53: error: implicit declaration of function ‘WLAN_FC_GET_STYPE’
/home/steve/ipwraw-ng/ipwraw.c:55: error: implicit declaration of function ‘WLAN_FC_GET_TYPE’
/home/steve/ipwraw-ng/ipwraw.c:56: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_FROMDS’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_TODS’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:58: error: ‘IEEE80211_4ADDR_LEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:59: error: ‘IEEE80211_STYPE_QOS_DATA’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:62: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:64: error: ‘IEEE80211_STYPE_CTS’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:65: error: ‘IEEE80211_STYPE_ACK’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:66: error: ‘IEEE80211_1ADDR_LEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:69: error: ‘IEEE80211_2ADDR_LEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘is_channel_a_band’:
/home/steve/ipwraw-ng/ipwraw.c:1709: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘is_channel_bg_band’:
/home/steve/ipwraw-ng/ipwraw.c:1714: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘store_channel’:
/home/steve/ipwraw-ng/ipwraw.c:1878: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:1884: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘store_band’:
/home/steve/ipwraw-ng/ipwraw.c:1926: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:1927: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_get_channel_info’:
/home/steve/ipwraw-ng/ipwraw.c:3284: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:3294: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘reg_get_chnl_grp_index’:
/home/steve/ipwraw-ng/ipwraw.c:3489: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_init_channel_map’:
/home/steve/ipwraw-ng/ipwraw.c:4111: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:4112: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_post_alive_work’:
/home/steve/ipwraw-ng/ipwraw.c:4248: error: ‘IEEE80211_OFDM_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:4249: error: ‘IEEE80211_OFDM_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:4250: error: ‘IEEE80211_CCK_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:4251: error: ‘IEEE80211_CCK_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_queue_tx_free_tfd’:
/home/steve/ipwraw-ng/ipwraw.c:5974: error: implicit declaration of function ‘ieee80211_get_hdrlen’
/home/steve/ipwraw-ng/ipwraw.c:5974: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c: In function ‘raw_rx’:
/home/steve/ipwraw-ng/ipwraw.c:6396: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6406: error: ‘ETH_P_80211_RAW’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: At top level:
/home/steve/ipwraw-ng/ipwraw.c:6416: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/steve/ipwraw-ng/ipwraw.c:6416: warning: its scope is only this definition or declaration, which is probably not what you want
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_data_packet’:
/home/steve/ipwraw-ng/ipwraw.c:6441: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c: At top level:
/home/steve/ipwraw-ng/ipwraw.c:6456: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/steve/ipwraw-ng/ipwraw.c: In function ‘is_duplicate_packet’:
/home/steve/ipwraw-ng/ipwraw.c:6458: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6459: error: implicit declaration of function ‘WLAN_GET_SEQ_SEQ’
/home/steve/ipwraw-ng/ipwraw.c:6460: error: implicit declaration of function ‘WLAN_GET_SEQ_FRAG’
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_tx’:
/home/steve/ipwraw-ng/ipwraw.c:6504: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6509: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6509: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6514: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6514: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6522: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6526: error: ‘IEEE80211_RADIOTAP_HDRLEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6540: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: At top level:
/home/steve/ipwraw-ng/ipwraw.c:6563: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_rx’:
/home/steve/ipwraw-ng/ipwraw.c:6618: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6623: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6623: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6628: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6628: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6646: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_reply_rx’:
/home/steve/ipwraw-ng/ipwraw.c:6852: error: variable ‘stats’ has initialiser but incomplete type
/home/steve/ipwraw-ng/ipwraw.c:6853: error: unknown field ‘rssi’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6853: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6853: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6854: error: unknown field ‘signal’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6854: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6854: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6855: error: unknown field ‘noise’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6855: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6855: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6856: error: unknown field ‘mac_time’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6856: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6856: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6857: error: unknown field ‘rate’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6857: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6857: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6858: error: unknown field ‘received_channel’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6858: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6858: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6859: error: unknown field ‘len’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6859: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6859: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6860: error: unknown field ‘freq’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6863: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6863: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6864: error: unknown field ‘tsf’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6864: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6864: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6865: error: unknown field ‘beacon_time’ specified in initialiser
/home/steve/ipwraw-ng/ipwraw.c:6865: warning: excess elements in struct initialiser
/home/steve/ipwraw-ng/ipwraw.c:6865: warning: (near initialisation for ‘stats’)
/home/steve/ipwraw-ng/ipwraw.c:6852: error: storage size of ‘stats’ isn’t known
/home/steve/ipwraw-ng/ipwraw.c:6881: error: ‘IEEE80211_STATMASK_RSSI’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6885: error: ‘IEEE80211_STATMASK_SIGNAL’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6887: error: ‘IEEE80211_STATMASK_NOISE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6889: error: ‘IEEE80211_STATMASK_RATE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:6852: warning: unused variable ‘stats’
/home/steve/ipwraw-ng/ipwraw.c: At top level:
/home/steve/ipwraw-ng/ipwraw.c:7256: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_rate’:
/home/steve/ipwraw-ng/ipwraw.c:7263: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7264: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7295: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7302: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7303: error: ‘IEEE80211_STYPE_AUTH’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7304: error: ‘IEEE80211_STYPE_DEAUTH’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7305: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7306: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: At top level:
/home/steve/ipwraw-ng/ipwraw.c:7333: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_basic’:
/home/steve/ipwraw-ng/ipwraw.c:7340: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7340: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7341: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7345: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7354: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7354: error: ‘IEEE80211_FCTL_MOREFRAGS’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7359: error: ‘IEEE80211_FCS_LEN’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7366: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7366: error: ‘IEEE80211_FCTL_PROTECTED’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7382: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7383: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7384: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7385: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7386: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘tx_skb’:
/home/steve/ipwraw-ng/ipwraw.c:7420: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7422: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7423: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7430: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7439: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7491: warning: passing argument 3 of ‘ipw_build_tx_cmd_basic’ from incompatible pointer type
/home/steve/ipwraw-ng/ipwraw.c:7493: warning: passing argument 3 of ‘ipw_build_tx_cmd_rate’ from incompatible pointer type
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_net_hard_start_xmit’:
/home/steve/ipwraw-ng/ipwraw.c:7562: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_hdr_1addr’ 
/home/steve/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:7582: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7583: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c:7586: error: dereferencing pointer to incomplete type
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_prom_alloc’:
/home/steve/ipwraw-ng/ipwraw.c:8374: error: ‘ARPHRD_IEEE80211_RADIOTAP’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_wx_set_freq’:
/home/steve/ipwraw-ng/ipwraw.c:8517: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:8523: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/steve/ipwraw-ng/ipwraw.c:8870: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:8872: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/steve/ipwraw-ng/ipwraw.c:8902: error: ‘ARPHRD_IEEE80211’ undeclared (first use in this function)
make[2]: *** [/home/steve/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/steve/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-02063003-generic'
make: *** [modules] Error 2

```

...what the hell happened?

---

### Post by P4man on 2009-09-01
you shouldn't need 'sudo' for make, and Im not sure why you added the shell parameter at the end. Not that I think either explains your errors.. Im guessing that "fix" doesn't work with the kernel you're using, try an older kernel perhaps?

---

