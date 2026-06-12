---
title: "WiFi drops out in Ubuntu but not in Windows???"
date: 2010-07-23
forum: General Help
---

### Post by oxf on 2010-07-23
I'm travelling right now so am not connecting into my normal router. When using Ubuntu it connects to the Wifi and then after about 15 secs drops me out again. I I boot to Windows XP this doesnt happen.
 
Any sugestions where I should start looking tofigure out the problem? I'd much prefer to use linux
 
Thanks

---

### Post by iponeverything on 2010-07-23
Hi Mike, no clues to let us help you? The "it works in windows" is not quite enough..

---

### Post by oxf on 2010-07-23
> **iponeverything said:**
> Hi Mike, no clues to let us help you? The "it works in windows" is not quite enough..
 
Well I'd give some any sugestions what I should provide. It seems to be someting with ths router as others havn't had this problem. Maybe another router on the same channel perhaps?

---

### Post by Pontus Ohman on 2010-07-23
Is it a Dead-Link (D-Link)?! Because D-Link can't handle Ubuntu so good O_o

---

### Post by oxf on 2010-07-23
> **Pontus Ohman said:**
> Is it a Dead-Link (D-Link)?! Because D-Link can't handle Ubuntu so good O_o
 
No its a Speed Touch. But I didnt think the router would make any difference? could be wrong though

---

### Post by iponeverything on 2010-07-23
```

sudo lshw | head
sudo lshw -c Network
sudo lsusb
sudo lsmod

```

When connected:

```
sudo iwconfig
```

Right After a drop:

```
tail -v /var/log/messages /var/log/dmesg  /var/log/syslog /var/log/debug
sudo iwconfig

```

---

### Post by oxf on 2010-07-25
> **iponeverything said:**
> ```

sudo lshw | head
sudo lshw -c Network
sudo lsusb
sudo lsmod

```When connected:

```
sudo iwconfig
```Right After a drop:

```
tail -v /var/log/messages /var/log/dmesg  /var/log/syslog /var/log/debug
sudo iwconfig

```

Thhanks...OK it's stopped dropping now ( didn't do anything) but running very slow.

mbdb@Acer:~$ sudo lshw | head
[sudo] password for mbdb: 
acer                      
    description: Notebook
    product: AO532h
    vendor: Acer
    version: V1.08
    serial: LUSAQ0B1080015B9FE1601
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=FCD66C61-F008-11DE-A058-705AB6161E94
  *-core

mbdb@Acer:~$ sudo lshw -c Network
  *-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:16:1e:94
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:a0:62:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.105 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-5600ffff
mbdb@Acer:~$ 

mbdb@Acer:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mbdb@Acer:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
ppdev                   5259  0 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 306010  0 
snd_timer              19098  2 snd_pcm,snd_seq
i915                  285076  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
drm                   162377  4 i915,drm_kms_helper
intel_agp              24119  2 i915
acer_wmi               13861  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
serio_raw               3978  0 
cfg80211              126517  3 ath9k,mac80211,ath
led_class               2864  2 ath9k,acer_wmi
agpgart                31724  2 drm,intel_agp
atl1c                  28083  0 
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32168  2 
mbdb@Acer:~$ 

mbdb@Acer:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
ppdev                   5259  0 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 306010  0 
snd_timer              19098  2 snd_pcm,snd_seq
i915                  285076  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
drm                   162377  4 i915,drm_kms_helper
intel_agp              24119  2 i915
acer_wmi               13861  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
serio_raw               3978  0 
cfg80211              126517  3 ath9k,mac80211,ath
led_class               2864  2 ath9k,acer_wmi
agpgart                31724  2 drm,intel_agp
atl1c                  28083  0 
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32168  2 
mbdb@Acer:~$

---

### Post by bakegoodz on 2010-07-25
I may be a little familiar with your problem. A while back I dabbled with DIY Linux wireless router, before I got tired of the complexities and went with dd-wrt on a embedded router. What I found that the newer Atheros driver doesn't have things enabled that the Windows and the now less used Madwifi Linux driver (because it is not completely opensource) I don't remember what it was exactly called, but Atheros has a feature that can adapt to noisy and congested wifi environment that is not enabled in commonly used Linux driver. 
You could look for a Madwifi howto to use that driver, or figure out a way to get closer to the access point.

---

### Post by oxf on 2010-07-27
> **bakegoodz said:**
> I may be a little familiar with your problem. A while back I dabbled with DIY Linux wireless router, before I got tired of the complexities and went with dd-wrt on a embedded router. What I found that the newer Atheros driver doesn't have things enabled that the Windows and the now less used Madwifi Linux driver (because it is not completely opensource) I don't remember what it was exactly called, but Atheros has a feature that can adapt to noisy and congested wifi environment that is not enabled in commonly used Linux driver. 
You could look for a Madwifi howto to use that driver, or figure out a way to get closer to the access point.

Thanks for that. I'll research that more as I'm not familier with it. To be honest I'm not quite sure what my problem is or if I actually have one.

I purchased this Acer Aspire One notebook a couple of weeks before I left on this extended trip. Immediately installed Ubuntu 10.04 on it and was impressed how easy it installed and in particular that the Wireless card/driver was instantly recognised and work (my other laptop has the infamous Broadcom 43 series and required Ndiswrapper)

On my home system the WiFi works great but maybe that has to with the signal strength? Anyway now I'm away from home I've run into problems. The dropping I described on the OP was weird but now seems resolved. However, the connection speed is slow and may be nothing to do with me as it's also the case if I boot into Windows too. The signal strength is not great but acceptable just. 

The odd thing is that there's one websiite that Windows handles better that Ubuntu but otherwise its much the same. 

However, if there's anything that I can do to tweak or optimise my connection while I'm here I would like to try it. Bottom line is if the IP connection or the router is set up poorly its not my problem and not much I can do about it :(

---

### Post by oxf on 2010-07-28
OK I just done a side by side test without moving the notebook so I can assume the connection strength is the same and can rule that out as a factor.

Using it in Windows XP it loads web pages faster than in Linux. I did not notice any speed problems in Ubuntu on my home system or on another public system though. However, on this one it definately runs faster online using XP.

---

### Post by varunendra on 2010-07-29
You didn't post the output of iwconfig while it is connected and working.
```
iwconfig
```

It may help us determine if there is any packet-loss issue. In such a case it may be related with MTU as discussed [here]("http://ubuntuforums.org/showthread.php?t=1376506") (solved on page-3 of the thread).



Also, please post results within [ code] tags. To do so, highlight the pasted output text then click on the '#' icon at the top of editing window. Alternatively, you can simply type [ code] at the beginning and [ /code] at the end of the selected text. (don't use space within brackets)

It makes the result more readable.

---

### Post by oxf on 2010-07-29
> **varunendra said:**
> You didn't post the output of iwconfig while it is connected and working.
```
iwconfig
```It may help us determine if there is any packet-loss issue. In such a case it may be related with MTU as discussed [here]("http://ubuntuforums.org/showthread.php?t=1376506") (solved on page-3 of the thread).



Also, please post results within [ code] tags. To do so, highlight the pasted output text then click on the '#' icon at the top of editing window. Alternatively, you can simply type [ code] at the beginning and [ /code] at the end of the selected text. (don't use space within brackets)

It makes the result more readable.
  
OK sorry!
I should point out that I know the signal strength isn;t great but it does work quite abit better in Windows than Linux. I'd prefer to use Linx 

```
mbdb@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"12 Gods Resort"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:59:17:E7   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by varunendra on 2010-07-29
Oh, I thought iwconfig would be similar as ifconfig but it is not!
I was interested in sent/received/lost packets' info. Please post the results of ifconfig also:
```
ifconfig
```

Please run this command while the laptop is connected to internet.

---

### Post by oxf on 2010-07-30
Thanks :).....

```
mbdb@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:16:1e:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:a0:62:27  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::924c:e5ff:fea0:6227/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19371571 (19.3 MB)  TX bytes:4436355 (4.4 MB)

mbdb@Acer:~$ 

```

---

### Post by woohhaa on 2010-08-02
I am having a similar issue. My wifi connection works fine at home but at work it drops randomly. I know the wifi network is OK as all our manufacturing equipment (PC's and CNC machinery) hits it and continues to function. 

I have posted the requested output requested by other commenters below. 

Code:

[INDENT]cooley@QuiGon:~$ sudo lshw | head
quigon                    
    description: Portable Computer
    product: Latitude D610
    vendor: Dell Inc.
    serial: 16Q8481
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-3600-1051-8038-B1C04F343831
  *-core
       description: Motherboard
cooley@QuiGon:~$ sudo lshw -c Network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:11:55:78
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:0b:73:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.6.1.170 multicast=yes wireless=IEEE 802.11bg
cooley@QuiGon:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
cooley@QuiGon:~$ sudo lsmod
Module                  Size  Used by
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
joydev                  8708  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  285076  3 
b43                   163523  0 
dell_wmi                1793  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
mac80211              205146  1 b43
yenta_socket           20408  1 
ppdev                   5259  0 
dell_laptop             6856  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
rsrc_nonstatic         10015  1 yenta_socket
cfg80211              126517  2 b43,mac80211
intel_agp              24119  2 i915
soundcore               6620  1 snd
dcdbas                  5422  1 dell_laptop
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  1 b43
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ssb                    38671  1 b43
tg3                   109324  0 
____________________________________________________________

Connected

cooley@QuiGon:~$ sudo iwconfig
[sudo] password for cooley: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"******"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:BD:9B:54:25   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
___________________________________________________________

Disconnected

cooley@QuiGon:~$ tail -v /var/log/messages /var/log/dmesg  /var/log/syslog /var/log/debug
==> /var/log/messages <==
Aug  2 14:35:54 QuiGon kernel: [ 7966.204785] ata2: EH complete
Aug  2 14:46:50 QuiGon kernel: [ 8622.132398] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Aug  2 14:46:55 QuiGon kernel: [ 8627.132072] ata2.00: qc timeout (cmd 0xa0)
Aug  2 14:46:55 QuiGon kernel: [ 8627.132107] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Aug  2 14:47:00 QuiGon kernel: [ 8632.172190] ata2: link is slow to respond, please be patient (ready=0)
Aug  2 14:47:05 QuiGon kernel: [ 8637.156183] ata2: device not ready (errno=-16), forcing hardreset
Aug  2 14:47:05 QuiGon kernel: [ 8637.156199] ata2: soft resetting link
Aug  2 14:47:05 QuiGon kernel: [ 8637.336521] ata2.00: configured for UDMA/33
Aug  2 14:47:05 QuiGon kernel: [ 8637.336791] ata2: EH complete
Aug  2 15:51:40 QuiGon kernel: [12512.824212] composite sync not supported

==> /var/log/dmesg <==
[   12.449177] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   12.449880] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.450483] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.451268] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.461861] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   12.504766] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   12.511935] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   12.515230] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   12.764230] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   12.825775] ADDRCONF(NETDEV_UP): wlan0: link is not ready

==> /var/log/syslog <==
Aug  2 15:48:06 QuiGon kernel: [12299.108048] wlan0: direct probe to AP 00:22:bd:9b:01:d5 (try 2)
Aug  2 15:48:07 QuiGon kernel: [12299.308048] wlan0: direct probe to AP 00:22:bd:9b:01:d5 (try 3)
Aug  2 15:48:07 QuiGon kernel: [12299.508063] wlan0: direct probe to AP 00:22:bd:9b:01:d5 timed out
Aug  2 15:48:11 QuiGon NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug  2 15:48:11 QuiGon NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug  2 15:48:11 QuiGon NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug  2 15:48:11 QuiGon NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Aug  2 15:48:16 QuiGon wpa_supplicant[896]: Authentication with 00:00:00:00:00:00 timed out.
Aug  2 15:48:26 QuiGon NetworkManager: <info>  wlan0: link timed out.
Aug  2 15:51:40 QuiGon kernel: [12512.824212] composite sync not supported

==> /var/log/debug <==
Aug  2 15:47:45 QuiGon kernel: [12277.700043] wlan0: direct probe to AP 00:22:bd:9b:00:c5 timed out
Aug  2 15:47:55 QuiGon kernel: [12287.992801] wlan0: direct probe to AP 00:22:bd:9b:00:c5 (try 1)
Aug  2 15:47:56 QuiGon kernel: [12288.192045] wlan0: direct probe to AP 00:22:bd:9b:00:c5 (try 2)
Aug  2 15:47:56 QuiGon kernel: [12288.392042] wlan0: direct probe to AP 00:22:bd:9b:00:c5 (try 3)
Aug  2 15:47:56 QuiGon kernel: [12288.592050] wlan0: direct probe to AP 00:22:bd:9b:00:c5 timed out
Aug  2 15:48:06 QuiGon kernel: [12298.906165] wlan0: deauthenticating from 00:22:bd:9b:00:c5 by local choice (reason=3)
Aug  2 15:48:06 QuiGon kernel: [12298.908231] wlan0: direct probe to AP 00:22:bd:9b:01:d5 (try 1)
Aug  2 15:48:06 QuiGon kernel: [12299.108048] wlan0: direct probe to AP 00:22:bd:9b:01:d5 (try 2)
Aug  2 15:48:07 QuiGon kernel: [12299.308048] wlan0: direct probe to AP 00:22:bd:9b:01:d5 (try 3)
Aug  2 15:48:07 QuiGon kernel: [12299.508063] wlan0: direct probe to AP 00:22:bd:9b:01:d5 timed out

[/INDENT]

---

### Post by woohhaa on 2010-09-17
Anyone have a clue on this? I'm still at a loss.

---

### Post by cek on 2010-09-17
Aug 2 15:47:56 QuiGon kernel: [12288.192045] wlan0: direct probe to AP 00:22:bd:9b:00:c5 (try 2)


This is a similar problem as was raised in this thread:
[http://ubuntuforums.org/showthread.php?t=1454397](http://ubuntuforums.org/showthread.php?t=1454397)

I'm glad it appears to be happening on other devices than the Palm.

I've posted a workaround to this in that thread that involves getting the latest drivers from wireless.kernel.org and recompiling.  I also raised this to the wireless.kernel.org mailing list, but since it was (at that time) limited to the Palm Pre, it was regarded as a failing of the Palm hotspot application itself.


There appears to be some router implementations that don't properly respond to direct probe requests, and you have to send all probe requests to the router on the broadcast address.  Okay, I don't even know exactly what that means ;), but the workaround I posted in the above thread has been working for me for about 6 months, though the instructions have changed because there are significant differences in the wireless drivers from wireless.kernel.org.

Disclaimer:  My use case is a desktop machine and the Palm Pre is the only available internet connection I have -- so I don't know if this will be compatible with other routers/access points.

---

### Post by cek on 2010-10-01
This issue has been resolved in the latest drivers from wireless.kernel.org.

Just download and follow the building/installation instructions.

---

### Post by oxf on 2010-10-30
> **cek said:**
> Aug 2 15:47:56 QuiGon kernel: [12288.192045] wlan0: direct probe to AP 00:22:bd:9b:00:c5 (try 2)


This is a similar problem as was raised in this thread:
[http://ubuntuforums.org/showthread.php?t=1454397](http://ubuntuforums.org/showthread.php?t=1454397)

I'm glad it appears to be happening on other devices than the Palm.

I've posted a workaround to this in that thread that involves getting the latest drivers from wireless.kernel.org and recompiling.  I also raised this to the wireless.kernel.org mailing list, but since it was (at that time) limited to the Palm Pre, it was regarded as a failing of the Palm hotspot application itself.


There appears to be some router implementations that don't properly respond to direct probe requests, and you have to send all probe requests to the router on the broadcast address.  Okay, I don't even know exactly what that means ;), but the workaround I posted in the above thread has been working for me for about 6 months, though the instructions have changed because there are significant differences in the wireless drivers from wireless.kernel.org.

Disclaimer:  My use case is a desktop machine and the Palm Pre is the only available internet connection I have -- so I don't know if this will be compatible with other routers/access points.

Let me clarify, I am  -Not- using a palm just a standard laptop (Compaq). It would have been better to start a separate thread for the palm issue which is rather different.

Since that time, however,  I've not had a problem connecting with any other routers. This does not mean it's been resolved, but rather it crops up only very occasionally. From what I read It seems in general this type of problem (where you can connect using windows but the connection drops out or is slower in Linux) does exist and warrants further investigation. 

For me it's not an issue right now but no doubt one day I will encounter it again when travelling! I'd like to be better prepared to handle it when I do.

---

