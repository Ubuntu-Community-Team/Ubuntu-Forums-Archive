---
title: "Sound device not identified"
date: 2006-05-25
forum: General Help
---

### Post by salem7 on 2006-05-25
There is no sound at all! I tried alsamixer and it gave me the following:
```
alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
```
Guess the device is not identified.... how can i solve this? :confused:

---

### Post by tkjacobsen on 2006-05-25
try to  lspci  and see if the device is detected. If it is not, maybe you'll have to compile your own kernel with the correct  drivers. Else try
```
sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils

```

---

### Post by salem7 on 2006-05-26
This is what i get for lspci
```

0000:00:00.0 Host bridge: Intel Corporation 955X Memory Controller Hub
0000:00:01.0 PCI bridge: Intel Corporation 955X PCI Express Graphics Port
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (rev 80)
0000:01:00.1 Display controller: ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (Secondary) (rev 80)
0000:04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

```
I reconfigured alsa as mentioned but w/o success! How can i recompile the kernel? (I think its too much a solution just to get the sound working.... no easier solutions available!)

---

### Post by tkjacobsen on 2006-05-26
it shouldnt be nesessary to recompile the kernel. But I really can't figure out what the problem is...

Which sound card do you have. Maybe check out the package alsa-firmware-loaders.:
ALSA software loaders for specific hardware
A collection of software loaders for specific hardware:

 cspctl - Sound Blaster 16 ASP/CSP control program
 hdsploader - firmware loader for the RME Hammerfall DSP cards
 mixartloader - firmware loader for Digigram's miXart board sound drivers
 pcxhrloader - firmware loader for Digigram pcxhr compatible soundcards
 sscape_ctl - SoundScape control utility and firmware loader
 usx2yloader - firmware loader for Tascam USX2Y USB soundcards
 vxloader - firmware loader for Digigram VX soundcards

---

### Post by ibanez88 on 2007-07-20
Did you download and install the firmware separately? The loaders are included as packages but not the Alsa firmware itself.  Both are needed, provided that your card is supported by Alsa in the first place.  

Have you tried using a different driver (OSS, etc.)  in your sound preferences?

---

### Post by NilsE on 2007-07-20
In a terminal run: 

asoundconf list



This should return a list of cards.
 

In a terminal run: 

asoundconf set-default-card  xxxxxxx



Then again with sudo: 

sudo asoundconf set-default-card xxxxxx

xxxxx is the name of the card that showed up in the list command which I believe is case sensitive.


This will at least ensure the card is recognized and set it as the default.

---

