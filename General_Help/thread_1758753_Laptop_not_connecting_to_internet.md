---
title: "Laptop not connecting to internet"
date: 2011-05-15
forum: General Help
---

### Post by koolaidz83095 on 2011-05-15
Hi everyone. 

I recently installed Ubuntu 10.10 32bit onto my uncle's laptop. The laptop is a Acer Aspire 4720Z. The problem is that Ubuntu is not detecting anything that it can connect to for internet. When I click on the network manager icon, it only gives me the option to create a VPN which is not what we want to do. 

The first time I tried connecting the laptop wirelessly, it failed. I even tried connecting the laptop directly to our modem with an ethernet cable and it still did not connect for some reason. I have no clue what the problem might be. 

Any help is appreciated. 
Thanks!

---

### Post by mikewhatever on 2011-05-15
We'll need a moderate amount of technical info to be able to offer anything beyond commiseration. Since that laptop has no internet access at all, you'll have to use a usb stick and a text editor to copy/past outputs. Create a network.txt file on your Desktop, then use a terminal window to input the following commands, and past the outputs into the text file.
```

ifconfig

lspci

lsusb

lsmod
```

---

### Post by grahammechanical on 2011-05-15
Some laptops require a keyboard key combination to be pressed to switch on the networking adapters. Also, if networking has been switched off by MS Windows then it is often not activated when Ubuntu loads. When you right click the network manager icon, is there a tick mark against the lines Enable networking and Enable wireless? Clicking on those lines switches networking off and on and this sometimes activates the machine to try to make a connection.

Regards.

---

### Post by koolaidz83095 on 2011-05-15
> **mikewhatever said:**
> We'll need a moderate amount of technical info to be able to offer anything beyond commiseration. Since that laptop has no internet access at all, you'll have to use a usb stick and a text editor to copy/past outputs. Create a network.txt file on your Desktop, then use a terminal window to input the following commands, and past the outputs into the text file.

I'm not sure if this is what you needed but this is what came up for each command. Sorry if I'm not giving you the right info you need, I'm a noob when it comes to networking and such. 
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:cd:50:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:07:dd:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
joydev                  8735  0 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  290938  3 
drm_kms_helper         30200  1 i915
ath5k                 130051  0 
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231541  1 ath5k
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               55847  0 
drm                   168054  4 i915,drm_kms_helper
ath                     8153  1 ath5k
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144470  3 ath5k,mac80211,ath
r852                    9536  0 
sm_common               3285  1 r852
intel_agp              26360  2 i915
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
mtd                    18877  2 sm_common,nand
agpgart                32011  2 drm,intel_agp
psmouse                59033  0 
video                  18712  1 i915
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
sdhci_pci               6339  0 
tg3                   123310  0 
firewire_ohci          21106  0 
ahci                   19013  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
sdhci                  15890  1 sdhci_pci
led_class               2633  2 ath5k,sdhci
libahci                21667  2 ahci
```

[QUOTE=grahammechanical]Some laptops require a keyboard key combination to be pressed to switch  on the networking adapters. Also, if networking has been switched off by  MS Windows then it is often not activated when Ubuntu loads. When you  right click the network manager icon, is there a tick mark against the  lines Enable networking and Enable wireless? Clicking on those lines  switches networking off and on and this sometimes activates the machine  to try to make a connection.

Regards. 	[/QUOTE]
Enable Networking and Enable Wireless are both checked. 

Thanks.

---

### Post by kimhellbert on 2011-05-15
here i think that you should use some internet enquirers on other pc as to for your laptop and just try it by sharing i hope that if it will run so then after it can run without share also.:)

---

### Post by koolaidz83095 on 2011-05-15
> **kimhellbert said:**
> here i think that you should use some internet enquirers on other pc as to for your laptop and just try it by sharing i hope that if it will run so then after it can run without share also.:)
Do you mean connecting the laptop to a PC with internet connection? I've tried that. Nothing changes.

---

### Post by koolaidz83095 on 2011-05-15
bump

---

### Post by mikewhatever on 2011-05-15
I am not quite sure why it doesn't work, the wireless interface is up and the module is loaded. To further investigate the problem, can you post the output of the following:
```
dmesg | grep -e ath5k -e eth -e wlan
```

---

### Post by koolaidz83095 on 2011-05-16
I'm not sure how, but the problem seems to have fixed itself. The internet connection is really strong too. 

I still appreciate all the help though. 
Thanks!):P

---

### Post by mikewhatever on 2011-05-16
Glad it got fixed, and thanks for the update.O:)

---

