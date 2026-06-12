---
title: "Ubuntu randomly detects video card? Strange please help"
date: 2011-08-05
forum: General Help
---

### Post by gustokonyan on 2011-08-05
I have the same problem with this one [http://ubuntuforums.org/showthread.php?p=11043378](http://ubuntuforums.org/showthread.php?p=11043378)

My laptop is an Acer Aspire 4710, Mobile Intel Graphics Media Accelerator 950.

Here's the problem. After a fresh install, once or twice, Unity-compiz would work fine, but most of the time it won't. What happens is it boots until Ubuntu loading screen, and then very  discreet white lines flicker, and it is frozen. Sometimes it just boots  until loading screen then restarts itself..

I was able to boot it completely using the "nomodeset" fix i found  somewhere, but i think it completely disables unity. Compiz does not  work too. I tried running "compiz --replace" and gets the following  error message..

...
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session


It's just weird. It's as if it randomly detects the video card. lol

Can someone help please? thanks. :smile:

---

### Post by linuxuser12345 on 2011-08-05
Have you tried experimenting with other Ubuntu versions?

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands please:
```
lsmod
```
```
sudo lspci -k
```
```
lspci | grep VGA

```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by gustokonyan on 2011-08-05
@linuxuser12345
hi, i haven't. but i am planning to try the 11.10 alpha version. the threadstarter of the post i linked above mentioned the alpha version fixed his problem.

@wildmanne39
hi, thank you. here are the output
**lsmod**
```

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
iwl3945               126017  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
iwlcore               148965  1 iwl3945
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  450934  0 
mac80211              257001  2 iwl3945,iwlcore
drm_kms_helper         40745  1 i915
acer_wmi               23153  0 
sparse_keymap          13666  1 acer_wmi
uvcvideo               66851  0 
drm                   180037  2 i915,drm_kms_helper
cfg80211              156212  3 iwl3945,iwlcore,mac80211
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

```**sudo lspci -k**
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 012f
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel modules: i2c-i801
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 011c
    Kernel driver in use: tg3
    Kernel modules: tg3
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
0a:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
0a:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 012f
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
0a:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 012f


```**lspci | grep VGA**
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by wildmanne39 on 2011-08-06
Hi, run this command please:
```
/usr/lib/nux/unity_support_test -p
```
and post the results here.

I believe the problem is that your card is less supported in natty because of the age of the system.

---

### Post by gustokonyan on 2011-08-06
Here..

```
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

---

### Post by wildmanne39 on 2011-08-06
Hi, you can not run unity, so if it was loading it sometimes it was just a fluke.

You can install unity 2d with synaptic.

Or you can log into classic with no effects and it will probably work ok.

I am sorry I did not have better news.

---

### Post by gustokonyan on 2011-08-06
Hi, no worries. Thank you very much for taking your time to solve this. I really appreciate it!

I have tried unity-2d already. And uninstalled it right after..

Actually, i don't care about unity. I run ubuntu classic on my other laptop and i am very happy. What i really care about is running compiz animations on my Acer. Will that be possible in my case?

Again.. thanks a bunch :)

---

### Post by wildmanne39 on 2011-08-06
Hi, I do not think so.
Here is a guide you can use to try to setup things like the cube and effects.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

You can in 10.04 if you want to install it and it has longer support then 11.04.

---

### Post by gustokonyan on 2011-08-06
thank you wildmanne! i will give it a shot.

---

### Post by wildmanne39 on 2011-08-06
Hi, your welcome. Also if you try to use compiz in classic you need to look at this link first.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

In fact this might solve your problem.

---

