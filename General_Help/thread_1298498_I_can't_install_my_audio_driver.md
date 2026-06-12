---
title: "I can't install my audio driver"
date: 2009-10-22
forum: General Help
---

### Post by dbyjazz on 2009-10-22
I have a Gateway MX3228 Notebook and I've had this problem ever since I installed Ubuntu about 6 months ago and I've finally had enough. How the heck do I get my audio driver installed?! Nobody has been able to tell me what to do. Please help.

here is my sudo lspci just in case you need it.

```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
```

and here is my sudo lsmod

```
Module                  Size  Used by
rfkill_input           12800  0 
binfmt_misc            16776  1 
via                    49024  2 
drm                    96424  3 via
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
snd_atiixp_modem       20360  0 
snd_via82xx_modem      19336  5 
snd_intel8x0m          22028  0 
snd_ac97_codec        112292  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus                9856  1 snd_ac97_codec
snd_pcm                83076  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec
snd_timer              29704  1 snd_pcm
snd                    62756  14 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
b43                   131484  0 
pcmcia                 44748  0 
mac80211              217592  1 b43
pcspkr                 10496  0 
tifm_7xx1              13824  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
psmouse                61972  0 
cfg80211               38288  1 mac80211
via_agp                16256  1 
i2c_viapro             15892  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
tifm_core              15900  1 tifm_7xx1
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw              13444  0 
led_class              12036  1 b43
input_polldev          11912  1 b43
agpgart                42696  2 drm,via_agp
shpchp                 40212  0 
video                  25872  0 
output                 11008  1 video
usbhid                 42336  0 
via_rhine              30856  0 
mii                    13312  1 via_rhine
ssb                    41220  1 b43
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

I've already tried ```
cat /dev/urandom | aplay
``` and I can't hear anything :/

---

### Post by spiderbatdad on 2009-10-22
maybe a module here: [http://hardware4linux.info/module/VIA_82xx_Audio/](http://hardware4linux.info/module/VIA_82xx_Audio/)

---

### Post by spiderbatdad on 2009-10-22
package here:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
cho9ose ubuntu 9.04 from the dropdown list...not the open suse driver.

---

### Post by dbyjazz on 2009-10-22
thanks what about platform?

---

