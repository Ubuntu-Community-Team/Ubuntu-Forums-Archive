---
title: "Messed up graphics."
date: 2012-03-22
forum: General Help
---

### Post by even.mannerud on 2012-03-22
Im not sure what to call it but my screen is messed up after a fresh install, it looks kinda scrambled and gets worse the more i move the mouse around or click stuff.

here is a snapshot of the screen [https://www.dropbox.com/sh/8uv264zkcououpq/oDGTIMg8jg/2012-03-22%2018.01.11.jpg](https://www.dropbox.com/sh/8uv264zkcououpq/oDGTIMg8jg/2012-03-22%2018.01.11.jpg)

I've been googeling a lot but can't seem to find an answer. 
Ive tried both ubuntu and opensuse and i get the same resault. 

The computer i'm using is a laptop from pacard bell with a athlon 64 amd processor and an ati radeon graphics chip. 
I tried both 32 and 64 bit ubuntu.

Can anyone please point me in the right direction for finding a solution to my problem?

Thanx 
Even
Norway

---

### Post by 2F4U on 2012-03-22
What graphics driver are you using, open source or proprietary from ATI?

---

### Post by even.mannerud on 2012-03-22
good question.

Using the one that came with Ubuntu.

---

### Post by UltimateCat on 2012-03-22
Hi!
As an example I have the ATI Radeon 3100 Graphic's card so I went to this website for help and installed the right driver.

[http://www.official-drivers.com/installer/?seed=ati&gclid=CIOPm7iR-64CFQdN4AodnHzSwQ](http://www.official-drivers.com/installer/?seed=ati&gclid=CIOPm7iR-64CFQdN4AodnHzSwQ)

Hope this helps

---

### Post by even.mannerud on 2012-03-22
Here are copies of lspci and lsmod if that can be helpful.

lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

lsmod

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
snd_seq_midi_event     14899  1 snd_seq_midi
radeon               1015995  3 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
arc4                   12529  2 
uvcvideo               72711  0 
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               93004  1 uvcvideo
psmouse                73882  0 
ath9k                 127538  0 
v4l2_compat_ioctl32    17083  1 videodev
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
mac80211              310872  1 ath9k
edac_core              53746  0 
sp5100_tco             13791  0 
soundcore              12680  1 snd
k8temp                 13057  0 
edac_mce_amd           23709  0 
ath9k_common           13839  1 ath9k
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
ath9k_hw              312866  2 ath9k,ath9k_common
drm                   236330  5 radeon,ttm,drm_kms_helper
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
i2c_algo_bit           13423  1 radeon
video                  19412  0 
shpchp                 37345  0 
binfmt_misc            17540  1 
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
pata_atiixp            13164  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0

---

### Post by Mark Phelps on 2012-03-22
Radeon x1200 is considered a "legacy" chipset, meaning, there are no current restricted drivers for it.  Ubuntu installed the default open-source Radeon drivers for it when you first setup Ubuntu.  Those are the only drivers available now.  When you installed the other drivers, you made the situation worse, not better.

You will need to follow the instructions in the link below to remove those drivers and replace them with the open-source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

