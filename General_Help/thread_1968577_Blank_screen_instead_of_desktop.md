---
title: "Blank screen instead of desktop"
date: 2012-04-29
forum: General Help
---

### Post by ryanyeah on 2012-04-29
So I am looking to do some research into why I my computer hangs on a black screen with just a cursor showing, sometimes when I try and boot into Ubuntu. It seems I am able to switch to the tty command prompt but when I switch back to the desktop, it is still blank. This only happens some of the time and other times it will load just fine.

Anyone have any links to some good documentation that I'd be able to read up on in order to help diagnose this issue?

---

### Post by hal8000 on 2012-04-29
You need to state more details:

Ubuntu version and desktop
e.g.  12.04 and gnome-fallback, Unity, etc

Graphics card,
Driver in use.


Provide the output of:
lspci

and

lsmod

---

### Post by ryanyeah on 2012-04-29
> **hal8000 said:**
> 
Ubuntu version and desktop
e.g.  12.04 and gnome-fallback, Unity, etc 

Sorry about that. I'm running a fresh install of Ubuntu 12.04 (full format with no extra partitions). I don't actually run unity, as I switch to the regular gnome look from the options at the Ubuntu login screen.

> **hal8000 said:**
> 
Graphics card,
Driver in use. 

This is also a brand new computer build. It is currently using onboard graphics on an Asrock Z77 Extreme 4 motherboard. No drivers have been updated yet. Although, I am not sure how to do this Ubuntu as of yet, but judging from the Asrock driver download page, all their drivers are quoted for Windows.


> **hal8000 said:**
> Provide the output of:
lspci

> 
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller


> **hal8000 said:**
> lsmod

> 
$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mxm_wmi                12979  0 
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
tg3                   152032  0 


---

### Post by ryanyeah on 2012-04-30
So it would seem that if I type my password onto the blank screen and press enter, it then renders the login screen like normal the problem is related to graphics...

---

### Post by ryanyeah on 2012-05-02
bamp

---

