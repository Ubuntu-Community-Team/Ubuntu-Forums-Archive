---
title: "Wifi Driver Help"
date: 2012-05-15
forum: General Help
---

### Post by Spiffed0 on 2012-05-15
Hey guys, I am brand new to Ubuntu and Linux all together. I recently set up a dual boot with Ubuntu on my **ASUS U56E Notebook**. The problem is, whenever I boot with Ubuntu I can not connect to wireless networks. I have gone through countless forum posts and tutorials on how to get my wifi working. I was working through this ([https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)), But the drivers .inf files were not working for me. Any help would be greatly appreciated. 

Thanks.

Spiffed

---

### Post by dizignit on 2012-05-15
Can you provide the model number and manufacturer of the card you have on your system? In my experience Ubuntu does a pretty decent job finding drivers for the hardware on the system.

---

### Post by UltimateCat on 2012-05-15
To find out what card you have open a terminal by pressing :
Ctril + Alt+T down

When the terminal prompts you type in:

```
lspci

```The manufacturer and card will be listed by the terminal and than you'll know what card you have and persue the website for which driver you need.  

This website is good for people who are new to Linux and Ubuntu:
[http://www.makeuseof.com/tag/download-ubuntu-absolute-beginners-guide/](http://www.makeuseof.com/tag/download-ubuntu-absolute-beginners-guide/)

Sincerely,
Ultimate Cat

---

### Post by Spiffed0 on 2012-05-15
> **UltimateCat said:**
> To find out what card you have open a terminal by pressing :
Ctril + Alt+T down

When the terminal prompts you type in:

```
lspci

```The manufacturer and card will be listed by the terminal and than you'll know what card you have and persue the website for which driver you need.

Here is what I got.
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

```

Spiffed

---

### Post by josephmills on 2012-05-15
can we now see these commands plz 

```

lsmod 

```
```

lspci -nn | grep Wireless

```
```

rfkill list all

```

thanks

---

### Post by Spiffed0 on 2012-05-15
lsmod = 
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
joydev                 17393  0 
arc4                   12473  2 
asus_nb_wmi            12469  0 
asus_wmi               19333  1 asus_nb_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
wmi                    18744  1 asus_wmi
iwlagn                273944  0 
mac80211              272785  1 iwlagn
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  2 iwlagn,mac80211
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
mei                    36466  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
atl1c                  36638  0 
ahci                   21634  1 
libahci                25727  1 ahci
xhci_hcd               72915  0 

```

lspci -nn | grep Wireless = 
```

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)

```


rfkill list all =
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wimax: WiMAX
	Soft blocked: yes
	Hard blocked: no

```

Spiffed

---

### Post by josephmills on 2012-05-15
try this 
```
sudo rmmod asus_wmi
```
then 
```
sudo modprobe iwlagn
```
do you have wireless ? 
if not please run 
```
sudo modprobe asus_wmi
```
and post 
```
dmesg | grep iwl*
```

thanks

---

### Post by Spiffed0 on 2012-05-15
dmesg | grep iwl* =
```

spiffed@ubuntu:~$ dmesg | grep iwl*
[   12.804518] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.804521] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.804570] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.804581] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.804609] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   12.815262] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   12.815265] iwlagn 0000:02:00.0: Device SKU: 0X9
[   12.815267] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.829285] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.829380] iwlagn 0000:02:00.0: irq 51 for MSI/MSI-X
[   12.925184] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.937190] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.112201] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   27.412036] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   35.699849] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   43.931753] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   52.227534] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   60.499378] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   68.799122] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   77.070953] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1117.566358] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1125.822075] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1134.029834] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1142.185683] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1156.017081] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1164.184907] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[ 1172.388699] iwlagn 0000:02:00.0: fail to flush all tx fifo queues

```

---

### Post by josephmills on 2012-05-16
lets see 
```
uname -a 
```
```
lsb_release -a 
```

---

### Post by Spiffed0 on 2012-05-16
uname -a =
```

Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```

lsb_release -a =
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

```

Spiffed

---

### Post by josephmills on 2012-05-16
```
sudo apt-get install linux-backports-modules-cw-3.0.0-12-generic
```

then reboot 
then come back and paste
```
lsmod
```
and 
```
apt-cache policy show linux-backports-modules-cw*
```
thanks

---

### Post by Spiffed0 on 2012-05-16
sudo apt-get install linux-backports-modules-cw-3.0.0-12-generic = 

Is this supposed to happen?
```

ic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.0.0-12-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.0.0-12-generic'

```

---

### Post by Spiffed0 on 2012-05-16
lsmod = 
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
arc4                   12473  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
asus_nb_wmi            12469  0 
asus_wmi               19333  1 asus_nb_wmi
sparse_keymap          13658  1 asus_wmi
psmouse                73673  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
iwlagn                273944  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
mac80211              272785  1 iwlagn
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 iwlagn,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 asus_wmi
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
mei                    36466  0 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  1 
libahci                25727  1 ahci
xhci_hcd               72915  0 
atl1c                  36638  0 

```

apt-cache policy show linux-backports-modules-cw* = 
```

Installed: (none)
  Candidate: 3.0.0-16.9
  Version table:
     3.0.0-16.9 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-16-generic:
  Installed: (none)
  Candidate: 3.0.0-16.9
  Version table:
     3.0.0-16.9 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-16-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-16.9
  Version table:
     3.0.0-16.9 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-16-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-16.9
  Version table:
     3.0.0-16.9 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-17-generic:
  Installed: (none)
  Candidate: 3.0.0-17.10
  Version table:
     3.0.0-17.10 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-17-generic:
  Installed: (none)
  Candidate: 3.0.0-17.10
  Version table:
     3.0.0-17.10 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-17-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-17.10
  Version table:
     3.0.0-17.10 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-17-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-17.10
  Version table:
     3.0.0-17.10 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-19-generic:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-19-generic:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.3-3.0.0-19-generic:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-19-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-3.0.0-19-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.3-3.0.0-19-generic-pae:
  Installed: (none)
  Candidate: 3.0.0-19.12
  Version table:
     3.0.0-19.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-oneiric-generic:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-oneiric-generic-pae:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-oneiric-generic:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.2-oneiric-generic-pae:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.3-oneiric-generic:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.3-oneiric-generic-pae:
  Installed: (none)
  Candidate: 3.0.0.19.23
  Version table:
     3.0.0.19.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages
linux-backports-modules-cw-3.1-3.0.0-16-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.1-3.0.0-17-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.1-3.0.0-19-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.1-oneiric-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.2-3.0.0-16-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.2-3.0.0-17-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.2-3.0.0-19-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.2-oneiric-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.3-3.0.0-19-server:
  Installed: (none)
  Candidate: (none)
  Version table:
linux-backports-modules-cw-3.3-oneiric-server:
  Installed: (none)
  Candidate: (none)
  Version table:
N: Unable to locate package show


```

---

### Post by josephmills on 2012-05-16
no that is not  supposed to happen let see if thre was a typo on my end or if it is a different package with 11.10 
```
apt-cache search compat wireless | grep linux
```
thanks 
if you get nothing back 
open ubuntu software enter and in the top part go to 
edit-->softwaresources-->other software


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218044&stc=1&d=1337142136[/IMG]



[SIZE="3"]And Please make sure that these are checked 
[/SIZE]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218045&stc=1&d=1337142136[/IMG]

Then Run 
```
sudo apt-get update
```
then 
paste here 
```
apt-cache search compat wireless | grep linux
```

Thanks

---

### Post by josephmills on 2012-05-16
can we also see a 
```
sudo update-grub
```
thanks

---

### Post by Spiffed0 on 2012-05-16
apt-cache search compat wireless | grep linux =
```

linux-backports-modules-cw-3.1-3.0.0-16-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.1-3.0.0-17-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.1-3.0.0-19-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.2-3.0.0-16-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.2-3.0.0-17-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.2-3.0.0-19-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.3-3.0.0-19-generic - compat-wireless Linux modules for version 3.0.0 on x86/x86_64
linux-backports-modules-cw-3.1-3.0.0-16-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.1-3.0.0-17-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.1-3.0.0-19-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.2-3.0.0-16-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.2-3.0.0-17-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.2-3.0.0-19-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86
linux-backports-modules-cw-3.3-3.0.0-19-generic-pae - compat-wireless Linux modules for version 3.0.0 on x86

```

Spiffed

---

### Post by Spiffed0 on 2012-05-16
sudo update-grub = 
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found Windows Recovery Environment (loader) on /dev/sda1
Skipping Windows Recovery Environment (loader) on Wubi system
Found Windows 7 (loader) on /dev/sda2
Skipping Windows 7 (loader) on Wubi system
done

```

Spiffed

---

### Post by josephmills on 2012-05-16
Your kernel is kinda old lets see if we can fix that.
```
sudo apt-get update && sudo apt-get --yes upgrade
```

then run 
```
apt-cache search linux-image
```
and paste that here thanks.

---

### Post by Spiffed0 on 2012-05-16
Sorry for the AFK, I will run this in a few hours and get back to you.

Spiffed

P.S. Thanks for all the help so far.

---

### Post by Spiffed0 on 2012-05-16
apt-cache search linux-image = 
```

alsa-base - ALSA driver configuration files
linux-image-3.0.0-12-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-12-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-12-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-12-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image - Generic Linux kernel image.
linux-image-3.0.0-13-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-13-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-14-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-14-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-15-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-15-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-16-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-16-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-17-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-17-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-19-generic - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-3.0.0-19-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-13-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-14-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-15-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-16-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-17-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-3.0.0-19-virtual - Linux kernel image for version 3.0.0 on x86/x86_64
linux-image-extra-virtual - Linux kernel extra modules for virtual machines
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
linux-virtual - Complete Linux kernel for virtual machines
linux-image-3.0.0-13-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-3.0.0-14-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-3.0.0-15-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-3.0.0-16-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-3.0.0-17-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-3.0.0-19-generic-pae - Linux kernel image for version 3.0.0 on x86
linux-image-generic-pae - Generic Linux kernel image

```

Spiffed

---

