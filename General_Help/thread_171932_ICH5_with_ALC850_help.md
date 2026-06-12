---
title: "ICH5 with ALC850 help"
date: 2006-05-07
forum: General Help
---

### Post by gils0040 on 2006-05-07
I have recently installed dapper beta 2 after using 5.10 and 5.04 previously and switching back to windows because i can not figure out my audio problem. I have an ASUS P4P800-E Deluxe motherboard that has and integrated Intel ICH5 card with a Realtek ALC850 rev 0 chip for sound. The problem is that the audio is distorted and i can only get it to play out of the channels on my 5.1 setup (the front right and front left). I have tried all solutions mentioned in the forums that deal with the ICH5 card with no luck. below are readouts from lspci and lsmod | grep snd respectively. I should also note that Volume Control shows only Master, PCM, and PC Speaker. Any help is greatly appreciated. Thank you!

ben@nomad145-247:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:04.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:02:0a.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
0000:02:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)


ben@nomad145-247:~$ lsmod | grep snd
snd_usb_audio          83200  0
snd_intel8x0           35964  1
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96644  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd_usb_lib            18048  1 snd_usb_audio
snd_rawmidi            26848  1 snd_usb_lib
snd_seq_device          9228  1 snd_rawmidi
snd_hwdep               9952  1 snd_usb_audio
snd                    60004  12 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
soundcore              10784  1 snd
usbcore               137700  7 snd_usb_audio,snd_usb_lib,usblp,usb_storage,ehci_hcd,uhci_hcd

i realized that i posted this in the wrong section. ive moved it to hardware. sorry

---

