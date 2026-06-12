---
title: "Wireless/Ubuntu 10.04/Targa pc,AMD Athlon(tm)*2DualCore QL-60,1.96Ghz/Laptop/2GBram"
date: 2010-05-05
forum: General Help
---

### Post by mysiak on 2010-05-05
802.1 1bgn ITRR MinicardWirelessAdapter.
Hi I just installned ubuntu on my pc and I can connect via cable from my router but I cannot connect
via wireless using WPA2 personal shared key.Once I actually got connected after one of reboots but no more than that.It just keeps asking for key even tough I entered it.Any help apretiated/ubuntu novice.
------------------------$ lspci--------------------------
06:00.0 Network controller: RaLink RT2860
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
--------$ lsusb-----------
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
----------$ ifconfig-----------------
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9680 (9.6 KB)  TX bytes:9680 (9.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:92:c7:cd:7f  
          inet6 addr: fe80::21d:92ff:fec7:cd7f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1030890 (1.0 MB)  TX bytes:0 (0.0 B)
          Interrupt:18 
--------------$ iwconfig---------------
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 00:18:F8:E5:AE:38   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-40 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
------------$ lsmod--------------------------
Module                  Size  Used by
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_realtek   278890  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  8 
ipt_addrtype            2151  4 
xt_state                1490  7 
ip6table_filter         2887  1 
ip6_tables             19618  1 ip6table_filter
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
nf_nat                 19501  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12980  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73934  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2791  1 
ip_tables              18390  1 iptable_filter
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11072  0 
x_tables               22429  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
jmb38x_ms               8643  0 
nvidia              10799466  40 
psmouse                64608  0 
serio_raw               4918  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
memstick               10121  1 jmb38x_ms
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
rt2860sta             542482  1 
shpchp                 33679  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
r8169                  39554  0 
mii                     5237  1 r8169
ieee1394               94675  1 ohci1394
ahci                   37646  1 
----------------------$ dmesg | grep RT2860--/I tried with grep not sure if correct because I got this error:
[   14.574045] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
------------------$ dmesg---------------------------------
5] <-- RTMPAllocTxRxRingMemory, Status=0
[   14.574045] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   14.574050] 1. Phy Mode = 0
[   14.574051] 2. Phy Mode = 0
[   14.594395] 3. Phy Mode = 0
[   14.597748] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   14.597752] MCS Set = 00 00 00 00 00
[   14.599323] <==== RTMPInitialize, Status=0
[   14.599388] 0x1300 = 00073200
[   14.609750] r8169: eth0: link down
[   14.610286] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.794988] ppdev: user-space parallel port driver
[   18.320046] hda_codec: ALC888: BIOS auto-probing.
[   18.730143] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input8
[   19.694133] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   20.630034] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[   25.060019] wlan0: no IPv6 routers present
[   31.465889] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   31.466141] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   41.485112] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   41.485335] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   51.501964] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   51.502185] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   61.516876] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   61.517118] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   71.535716] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565
[   71.535947] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   81.549962] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 424
[   81.550326] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)


-----------$ sudo lshw -C network----------------------
*-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:1d:92:c7:cd:7f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:fe9f0000-fe9fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:4e:7e:ca
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:e800(size=256) memory:febff000-febfffff memory:faff0000-faffffff(prefetchable) memory:febc0000-febdffff(prefetchable)
-------------$ iwlist scan----------only shoeing my home network--
Cell 03 - Address: 00:18:F8:E5:AE:38
                    Protocol:802.11b/g
                    ESSID:"jahodienkovo"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-40 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
---------------------$ lsb_release -d-------------------
Description:    Ubuntu 10.04 LTS
-----------------$ uname -mr-----------------------
2.6.32-21-generic x86_64

---

### Post by mysiak on 2010-05-06
Hi its me again now I am connected again, just like that, without making any changes but I want to ask could it be that I probably intalled the 64 bit version of ubuntu and my wireless in the output of the terminal says is 32 bit? Could this be the mistake why it is happening? should I just then install the 32 bit version instead and it would work ? Am I getting ii right?

---

