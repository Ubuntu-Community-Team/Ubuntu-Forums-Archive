---
title: "Help Wireless Internet Ubuntu 10.04  Intel Problems"
date: 2010-11-13
forum: General Help
---

### Post by boo12345679 on 2010-11-13
Having some issues connecting with wireless Internet connection
All was ok on earlier versions of Ubuntu until upgrade to 10.04
It feels like it is connecting but I cant surf the net.
Wired connections works ok
wireless works ok for windows machine 
No problems with the hardware I just upgraded about an hour ago

I cant seem to copy and paste into this box so I have attached a .txt file of all output.

I have restarted the machine etc. etc.

I will have to move back again if I cant get this working.

I am a little bemused why something as simple as wireless will not work.

Any assistance much appreciated, spent too much time on this...much prefer to have spent it with my family !

Thank you

---

### Post by boo12345679 on 2010-11-20
Hi anyone any response on this please ? Thank you

---

### Post by boo12345679 on 2010-11-20
Not sure if this makes it easier ?

abc@abc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 5E:03:52:1F:6E:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"2WIRE450"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 1038236ms ago
                    IE: Unknown: 00083257495245343530
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C


          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:310688 (310.6 KB)  TX bytes:310688 (310.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:8f:96:71  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe8f:9671/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7833 (7.8 KB)
          Power Management:off
          
abc@abc:~$ lsmod|iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"2WIRE450"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5E:03:52:1F:6E:9B   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
abc@abc:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE          1419  1 
xt_state                1014  1 
ipt_REJECT              2004  2 
xt_tcpudp               1927  4 
iptable_filter          1302  1 
nf_nat_h323             5121  0 
nf_conntrack_h323      46894  1 nf_nat_h323
nf_nat_pptp             1996  0 
nf_conntrack_pptp       4681  1 nf_nat_pptp
nf_conntrack_proto_gre     3901  1 nf_conntrack_pptp
nf_nat_proto_gre        1271  1 nf_nat_pptp
nf_nat_tftp              728  0 
nf_conntrack_tftp       2905  1 nf_nat_tftp
nf_nat_sip              5574  0 
nf_conntrack_sip       18703  1 nf_nat_sip
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_conntrack_ftp        5361  1 nf_nat_ftp
iptable_nat             3752  1 
nf_nat                 16289  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10783  4 iptable_nat,nf_nat
nf_conntrack           63258  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
ip_tables              10460  2 iptable_filter,iptable_nat
x_tables               15921  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
nls_utf8                1069  1 
isofs                  30022  1 
aes_i586                7280  209 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
joydev                  8735  0 
snd_seq_midi_event      6047  1 snd_seq_midi
arc4                    1165  2 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwl3945                85550  0 
iwlcore               127415  1 iwl3945
soundcore                880  1 snd
uvcvideo               55847  0 
psmouse                59033  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
videodev               43098  1 uvcvideo
serio_raw               4022  0 
mac80211              231541  2 iwl3945,iwlcore
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144470  3 iwl3945,iwlcore,mac80211
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  291004  3 
drm_kms_helper         30200  1 i915
drm                   168054  4 i915,drm_kms_helper
ahci                   19013  0 
r8169                  36489  0 
libahci                21667  3 ahci
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
mii                     4425  1 r8169
intel_agp              26360  2 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video

---

### Post by boo12345679 on 2010-11-20
Or this
abc@abc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"2WIRE450"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5E:03:52:1F:6E:9B   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

abc@abc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:4c:54:32  
          inet6 addr: fe80::21e:33ff:fe4c:5432/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3694 (3.6 KB)  TX bytes:7722 (7.7 KB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:313600 (313.6 KB)  TX bytes:313600 (313.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:8f:96:71  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe8f:9671/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7833 (7.8 KB)

abc@abc:~$ sudo dhclient -r
sudo password for abc: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit 

Listening on LPF/eth0/00:1e:33:4c:54:32
Sending on   LPF/eth0/00:1e:33:4c:54:32
Listening on LPF/wlan0/00:1f:3c:8f:96:71
Sending on   LPF/wlan0/00:1f:3c:8f:96:71
Sending on   Socket/fallback
abc@abc:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit 


Listening on LPF/eth0/00:1e:33:4c:54:32
Sending on   LPF/eth0/00:1e:33:4c:54:32
Listening on LPF/wlan0/00:1f:3c:8f:96:71
Sending on   LPF/wlan0/00:1f:3c:8f:96:71
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
^C
abc@abc:~$ ifdown wlan0
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
abc@abc:~$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
abc@abc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"2WIRE450"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5E:03:52:1F:6E:9B   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

abc@abc:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         
abc@abc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Golan Network Connection (rev 02)

abc@abc:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:4c:54:32
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:4000(size=256) memory:90010000-90010fff memory:90000000-9000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Golan Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:8f:96:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:94300000-94300fff


abc@abc:~$ uname -a
Linux abc 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by boo12345679 on 2010-11-20
Or this ?

abc@abc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:69:3A:02:64
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKY00611"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000041a3acd2008
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 0008534B593030363131
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:0D:72:E5:01:E1
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001751d3122
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B962C0C1218
                    IE: Unknown: 030103
                    IE: Unknown: 050400010100
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 3205243048606C
          Cell 03 - Address: 9E:51:2F:EE:8B:DB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"2WIRE450"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 26352ms ago
                    IE: Unknown: 00083257495245343530
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 1C:AF:F7:66:C3:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"virgin broadband"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001eb69cf17fc
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 001076697267696E2062726F616462616E64
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 05 - Address: 00:27:19:C5:7A:5C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BIGAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000069e9ff98e3e
                    Extra: Last beacon: 10176ms ago
                    IE: Unknown: 0005424947414C						
                    IE: Unknown: 010882848B960C121824						
                    IE: Unknown: 030101						
                    IE: WPA Version 1						
                        Group Cipher : TKIP						
                        Pairwise Ciphers (1) : TKIP						
                        Authentication Suites (1) : PSK						
                    IE: Unknown: 050400010000						
                    IE: Unknown: 2A0104						
                    IE: Unknown: 32043048606C

---

### Post by boo12345679 on 2010-11-28
Just to outline - I managed to sort this problem out without the use of windows wrappers.  At least I think so.

There seems to be a clash with "connman" so uninstall this and also install wi-cd and wi-fi radar.  

Mess around with the settings and hey presto it worked. 

This was through pure trial and error.  

I also installed rfkill but did not need to use it.

If anyone is stuck on this I will be happy to dump a load of command line outputs if it assits anyone else.

---

