---
title: "Can't get  wireless to work in Ubuntu 11.10 (rtl8192ce)"
date: 2012-04-06
forum: General Help
---

### Post by sno42 on 2012-04-06
I'm quiet new in Ubuntu. But problem is I can't get wireless to work. Tried to install driver for rtl8192ce -nothing. Maybe someone can help?

---

### Post by wildmanne39 on 2012-04-06
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sno42 on 2012-04-07
#
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux kaida-W240BU 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux

03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller [197b:0260] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:4510]
    Kernel driver in use: jme
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9196]
    Kernel driver in use: rtl8192ce

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254163  1 
snd_hda_codec_hdmi     31426  1 
sp5100_tco             13495  0 
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
arc4                   12473  2 
rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95614  1 rtl8192ce
psmouse                73673  0 
k10temp                12990  0 
mac80211              393421  3 rtl8192ce,rtl8192c_common,rtlwifi
serio_raw              12990  0 
snd_hda_intel          24262  2 
btusb                  18160  2 
snd_hda_codec          91859  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
cfg80211              172427  2 rtlwifi,mac80211
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
snd_seq_midi           13132  0 
i2c_piix4              13093  0 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
video                  18908  0 
wmi                    18744  0 
radeon                929507  3 
snd                    55902  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
soundcore              12600  1 snd
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
jme                    40330  0 
ahci                   21634  2 
libahci                25727  1 ahci

That should be all information I got. Thanks

---

### Post by wildmanne39 on 2012-04-07
Hi, it says that the wireless is turned off, use the keys or the switch on the computer to turn it on and see if that helps, if not we will go from there.
Thanks

---

### Post by leopoldbirkholm on 2012-04-07
What for type of computer do you have?

I have an Asus Eee PC 1001 and for me to toggle the WiFi on or off, I use FN+F2 key.

---

### Post by wildmanne39 on 2012-04-07
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
lsmod | grep rtl
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

