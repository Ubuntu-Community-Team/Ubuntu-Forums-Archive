---
title: "wireless for compaq presario v2000"
date: 2011-07-22
forum: General Help
---

### Post by yilin on 2011-07-22
I just installed ubuntu 11.04 to compaq presario v2000.

Everything works except wireless. Any advises? Thanks

---

### Post by wildmanne39 on 2011-07-22
Hi, run these commands in a terminal please
```
lspci -nn
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mdkathon on 2011-07-30
ken@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
05:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
ken@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


ken@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ken@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
radeon                900494  3 
snd_atiixp             19400  2 
snd_atiixp_modem       18624  5 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
pcmcia                 39671  0 
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
tifm_7xx1              12898  0 
yenta_socket           27230  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
snd                    55295  20 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
k8temp                 12872  0 
i2c_algo_bit           13184  1 radeon
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
video                  18951  0 
serio_raw              12990  0 
shpchp                 32345  0 
ati_agp                13202  0 
i2c_piix4              13095  0 
arc4                   12473  2 
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  1 
ken@ubuntu:~$

---

### Post by mdkathon on 2011-07-30
When I open the network manager dropdown on the top right of my desktop it shows Wireless Networking but is grayed out and has this "device not ready (firmware missing)".

---

### Post by wildmanne39 on 2011-07-30
Hi, open syanptic type bcm into search and uninstall anything there that has a small green square by it then close synaptic.

Run  this command
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
disconnect your wired connection then restart your system and you should have wireless.
Thank you

---

### Post by mdkathon on 2011-08-05
> **wildmanne39 said:**
> Hi, open syanptic type bcm into search and uninstall anything there that has a small green square by it then close synaptic.

Run  this command
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
disconnect your wired connection then restart your system and you should have wireless.
Thank you

This worked for me. Thanks! Wireless is working now. 

FYI: I did not see any "small green squares" in synaptic. So I just ran the apt-get in terminal and rebooted. 

Thanks again!

---

### Post by wildmanne39 on 2011-08-05
Hi, your welcome! I am glad you got it working.

---

### Post by nouveausouth on 2011-09-12
Please help...

I was following this thread, removed all green boxes, and now my computer only goes to Memtest when it restarts. I have no idea what I removed, but there are some files I created in Ubuntu that I need to recover. HELP!

---

### Post by gandaran on 2011-09-12
> **nouveausouth said:**
> Please help...

I was following this thread, removed all green boxes, and now my computer only goes to Memtest when it restarts. I have no idea what I removed, but there are some files I created in Ubuntu that I need to recover. HELP!
did you remove every package installed? you where supposed to remove only the broadcom drivers installed
to recover your files boot the live cd or usb drive then you can copy the files from the hard-drive

---

### Post by DrStankface on 2011-11-19
Okay so i'm having a bit of an issue as well. I've done all that was advised above but am still unable to connect. It seems as if it's establishing a connection but then fails at the last second. I enter the correct password for my router and when I look at the properties of the connection it shows a password that's incredibly long that I did not enter. Any advice?

---

### Post by TinMan77 on 2012-08-26
> **Wild Man said:**
> Hi, open syanptic type bcm into search and uninstall anything there that has a small green square by it then close synaptic.

Run  this command
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```disconnect your wired connection then restart your system and you should have wireless.
Thank you

This worked great!! I also have a compaq v2000 and could never get the wireless to work till now. I now have 12.04 running with mate desktop. Much better faster then it was with xp.

---

