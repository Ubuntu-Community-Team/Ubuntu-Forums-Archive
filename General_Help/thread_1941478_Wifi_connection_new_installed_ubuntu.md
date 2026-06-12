---
title: "Wifi connection new installed ubuntu"
date: 2012-03-15
forum: General Help
---

### Post by Lunemus on 2012-03-15
Hello everyone, I just recently manage to run ubuntu in my laptop. It's the the only  OS in it atm. I'm trying to find out how can i connect to my home connection via wifi. My wifi is "ON" in my laptop, but when i click the top right panel for wifi . I dont see any connection available. It's like it's not scanning for connections.

---

### Post by TeoBigusGeekus on 2012-03-15
Have you searched in Additional Drivers whether there is a proprietary driver for your wireless card?

---

### Post by Lunemus on 2012-03-15
I just looked, and all I have is nvidia drivers and a software modem.. When I try to activate them I get a msg say installation failure please have a look at the log file for details /var/log/jockey. Log

---

### Post by wildmanne39 on 2012-03-15
Hi, if there are no additional drivers for your card please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Lunemus on 2012-03-15
conrad@conrad-D900T:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux conrad-D900T 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
conrad@conrad-D900T:~$ lspci -nnk | grep -iA2 net
0a:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0900]
    Kernel driver in use: r8169
--
0a:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. Aspire 3022WLMi, 5024WLMi, 5020 [1468:0311]
    Kernel driver in use: b43-pci-bridge
conrad@conrad-D900T:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
conrad@conrad-D900T:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
conrad@conrad-D900T:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
arc4                   12473  2 
ppdev                  12849  0 
b43                   318816  0 
pcmcia                 39822  0 
mac80211              393421  1 b43
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
cfg80211              172427  2 b43,mac80211
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
joydev                 17393  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
nouveau               663226  3 
irda                  185428  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
crc_ccitt              12595  1 irda
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
ttm                    65224  1 nouveau
parport_pc             32114  1 
drm_kms_helper         32889  1 nouveau
drm                   192194  5 nouveau,ttm,drm_kms_helper
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
uas                    17699  0 
floppy                 60310  0 
firewire_ohci          35854  0 
r8169                  43104  0 
sata_promise           18006  2 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50682  1 b43
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
conrad@conrad-D900T:~$

---

### Post by wildmanne39 on 2012-03-15
Hi, this should get your wireless working but if it does not then we will troubleshoot it.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then unplug your wired connection and reboot.
Thanks

---

### Post by Lunemus on 2012-03-15
SOLVED!!!!!! Thank you very much sir it worked! i can finally see available connectivity including my home wifi.

---

### Post by wildmanne39 on 2012-03-15
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

