---
title: "HP G60 Laptop and headphones &gt;:-("
date: 2010-03-30
forum: General Help
---

### Post by tylerhughes on 2010-03-30
hey everyone,
I have searched for HOURS and HOURS on this forum as well as the rest of the interweb but I cannot, for the life of me, figure out how to get the speakers to mute when insert headphones!!!!! I do not have a headphone option in alsamixer nor anywhere else! Needless to say this is VERY frustrating!

Can somebody please help me out? Much appreciated! :P

---

### Post by tylerhughes on 2010-03-30
Also on this machine I have Win7 dual-boot and it works fine in windoze

---

### Post by avilella on 2010-03-31
Some other people have reported about sound issues. Here are the possible solutions in the forums:
[http://ubuntuforums.org/showpost.php?p=7405637&postcount=3](http://ubuntuforums.org/showpost.php?p=7405637&postcount=3)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

> **tylerhughes said:**
> Also on this machine I have Win7 dual-boot and it works fine in windoze

---

### Post by tylerhughes on 2010-03-31
> **avilella said:**
> Some other people have reported about sound issues. Here are the possible solutions in the forums:
[http://ubuntuforums.org/showpost.php?p=7405637&postcount=3](http://ubuntuforums.org/showpost.php?p=7405637&postcount=3)
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

thank you for your help; i had not come across either of these before
unfortunately, neither worked :( the 2nd one didnt even come close to working, i got errors on every single step

---

### Post by tylerhughes on 2010-04-04
bump?

---

### Post by 2hot6ft2 on 2010-04-04
I just tried it on mine and it worked like it should. Guess that doesn't help any. G60-125NR, NVIDIA Go 8200M, AMD Turion X2, Atheros AR5009.

It might help if you posted some specs. since there are about 100 models of G60 and many different hardware configurations.

---

### Post by tylerhughes on 2010-04-04
> **2hot6ft2 said:**
> 
It might help if you posted some specs. since there are about 100 models of G60 and many different hardware configurations.

;) well all i know about it is it's a G60-519WM with intel celeron 900......does that help any?? haha
how do i find out the specs of this particulat machine? thanks!

---

### Post by miegiel on 2010-04-06
> **tylerhughes said:**
> ;) well all i know about it is it's a G60-519WM with intel celeron 900......does that help any?? haha
how do i find out the specs of this particulat machine? thanks!

In a terminal
```
uname -srvmpio
sudo lshw -short
```
will tell you some.

example:
```
user@machine:~$ uname -srvmpio
 ________________________________________
/ Linux 2.6.32-19-generic-pae #28-Ubuntu \
| SMP Wed Mar 31 18:57:46 UTC 2010 i686  |
\ unknown unknown GNU/Linux              /
 ----------------------------------------
        \   ^__^
         \  (OO)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

user@machine:~$ sudo lshw -short
H/W path               Device     Class       Description
=========================================================
                                  system      Aspire 3810T
/0                                bus         Aspire 3810T
/0/0                              memory      1MiB BIOS
/0/f                              memory      4GiB System Memory
/0/f/0                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/f/1                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/17                             processor   Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
/0/17/18                          memory      3MiB L2 cache
/0/17/1a                          memory      32KiB L1 cache
/0/17/0.1                         processor   Logical CPU
/0/17/0.2                         processor   Logical CPU
/0/19                             memory      32KiB L1 cache
/0/100                            bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                          display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                        display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/1a                         bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                       bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                         multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                         bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c/0            wlan0      network     Wireless WiFi Link 5100
/0/100/1c.2                       bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.2/0          eth0       network     AR8131 Gigabit Ethernet
/0/100/1d                         bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                       bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                       bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.3                       bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1d.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      ICH9M-E LPC Interface Controller
/0/100/1f.2            scsi1      storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0.0.0      /dev/sda   disk        320GB WDC WD3200BJKT-0
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      64GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      234GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5  volume      4094MiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0/2/6  /dev/sda6  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/7  /dev/sda7  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/8  /dev/sda8  volume      206GiB Linux filesystem partition
/0/100/1f.3                       bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                       generic     82801I (ICH9 Family) Thermal Subsystem
/1                     vboxnet0   network     Ethernet interface
```

---

### Post by miegiel on 2010-04-06
> **tylerhughes said:**
> hey everyone,
I have searched for HOURS and HOURS on this forum as well as the rest of the interweb but I cannot, for the life of me, figure out how to get the speakers to mute when insert headphones!!!!! I do not have a headphone option in alsamixer nor anywhere else! Needless to say this is VERY frustrating!

Can somebody please help me out? Much appreciated! :P

I thought all laptops built this millennium had a switch to automatically switch the output to the headphones as soon as you plug something into the jack.

> **tylerhughes said:**
> Also on this machine I have Win7 dual-boot and it works fine in windoze

Do you mean with *"it works fine"* that it works as I described above, or that you have a speakers-out and a seperate headphone-out in win7?

---

### Post by tylerhughes on 2010-04-06
sudo lshw gave me
```
                               system      HP G60 Notebook PC
/0                             bus         3612
/0/0                           memory      1MiB BIOS
/0/13                          memory      3GiB System Memory
/0/13/0                        memory      2GiB SODIMM DDR2 Synchronous 800 MHz 
/0/13/1                        memory      1GiB SODIMM DDR2 Synchronous 800 MHz 
/0/1c                          processor   Intel(R) Celeron(R) CPU          900 
/0/1c/1d                       memory      1MiB L2 cache
/0/1c/1f                       memory      32KiB L1 cache
/0/1e                          memory      32KiB L1 cache
/0/100                         bridge      Mobile 4 Series Chipset Memory Contro
/0/100/2                       display     Mobile 4 Series Chipset Integrated Gr
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Gr
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c/0        eth0        network     RTL8101E/RTL8102E PCI Express Fast Et
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1/0      wmaster0    network     AR9285 Wireless Network Adapter (PCI-
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        250GB WDC WD2500BEVT-6
/0/100/1f.2/0/1    /dev/sda1   volume      199MiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume      120GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume      11GiB Windows NTFS volume
/0/100/1f.2/0/4    /dev/sda4   volume      99GiB Extended partition
/0/100/1f.2/0/4/5  /dev/sda5   volume      95GiB Linux filesystem partition
/0/100/1f.2/0/4/6  /dev/sda6   volume      4157MiB Linux swap / Solaris partitio
/0/100/1f.2/1      /dev/cdrom  disk        DVD RW AD-7581S
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                    generic     82801I (ICH9 Family) Thermal Subsyste
/1                             power       OEM_Define4

```

[QUOTE=miegiel]Do you mean with "it works fine" that it works as I described above, or that you have a speakers-out and a seperate headphone-out in win7?[/QUOTE]
yes, in windows it automatically switches to headphone output when headphones are inserted

---

### Post by lidex on 2010-04-06
You need to tell the alsa driver where the pins are.
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by tylerhughes on 2010-04-06
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Apr  7 01:34:40 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP G60 Notebook PC


!!Kernel Information
!!------------------

Kernel release:    2.6.31-20-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4700000 irq 29


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 103c:360b


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack-dig
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N
snd-hda-intel: model=laptop enable=1 index=0


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : 0,-1,-1,-1,-1,-1,-1,-1
	model : laptop,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0
	power_save : 10
	power_save_controller : N
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20583 (Pebble HSF)
Address: 0
Function Id: 0x2
Vendor Id: 0x14f15067
Subsystem Id: 0x103c360b
Revision Id: 0x100301
Modem Function Group: 0x2
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x49
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x50 0x50] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18 0x23 0x24*
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18* 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b 0x1d 0x1e*
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="Conexant Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Apr  6 21:17 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Apr  6 21:17 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 Apr  6 21:17 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Apr  6 21:17 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 Apr  6 21:17 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  1 Apr  6 21:16 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Apr  6 21:16 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr  6 21:17 .
drwxr-xr-x 3 root root 200 Apr  6 21:17 ..
lrwxrwxrwx 1 root root  12 Apr  6 21:17 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4700000 irq 29'
  Mixer name	: 'Conexant CX20583 (Pebble HSF)'
  Components	: 'HDA:14f15067,103c360b,00100301'
  Controls      : 12
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 0 [0%] [-74.00dB] [on]
  Front Right: Playback 0 [0%] [-74.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 17 [7%] [-47.60dB]
  Front Right: Playback 17 [7%] [-47.60dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Ext Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '30dB'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 0
		value.1 0
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '10dB'
		comment.item.2 '20dB'
		comment.item.3 '30dB'
		comment.item.4 '40dB'
		iface MIXER
		name 'Ext Mic Boost Capture Enum'
		value '30dB'
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Capture Volume'
		value.0 80
		value.1 80
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic B'
		comment.item.1 'Mic C'
		comment.item.2 'Mic E'
		comment.item.3 'Mic F'
		iface MIXER
		name 'Capture Source'
		value 'Mic B'
	}
	control.12 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 17
		value.1 17
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cbc
cryptd
aes_x86_64
aes_generic
dm_crypt
binfmt_misc
ppdev
joydev
snd_hda_codec_conexant
arc4
ecb
iptable_filter
snd_hda_intel
snd_hda_codec
snd_hwdep
ip_tables
x_tables
snd_pcm_oss
snd_mixer_oss
ath9k
mac80211
led_class
ath
snd_pcm
psmouse
serio_raw
snd_seq_dummy
snd_seq_oss
cfg80211
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
lp
parport
fbcon
tileblit
font
bitblit
softcursor
usbhid
r8169
mii
i915
drm
i2c_algo_bit
intel_agp
video
output


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x400001f0
0x1b 0x04a190f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x95a701f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    3.847102] i2c-adapter i2c-2: unable to read EDID block.
[    3.847107] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    4.428620] [drm] TV-20: set mode NTSC 480i 0
--
[   17.204876]   alloc kstat_irqs on node 0
[   17.204883] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.204939]   alloc irq_desc for 29 on node 0
[   17.204941]   alloc kstat_irqs on node 0
[   17.204951] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
[   17.204984] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.231032] phy0: Selected rate control algorithm 'ath9k_rate_control'
--
[   18.656046] i2c-adapter i2c-2: unable to read EDID block.
[   18.656050] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.660588] i2c-adapter i2c-2: unable to read EDID block.
[   18.660590] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.713769] [drm] TV-20: set mode NTSC 480i 0
--
[   19.117292] i2c-adapter i2c-2: unable to read EDID block.
[   19.117297] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.121984] i2c-adapter i2c-2: unable to read EDID block.
[   19.121987] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.168018] [drm] TV-20: set mode NTSC 480i 0
--
[   21.317773] i2c-adapter i2c-2: unable to read EDID block.
[   21.317776] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.322473] i2c-adapter i2c-2: unable to read EDID block.
[   21.322475] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.368496] [drm] TV-20: set mode NTSC 480i 0
--
[   21.759640] i2c-adapter i2c-2: unable to read EDID block.
[   21.759644] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.764315] i2c-adapter i2c-2: unable to read EDID block.
[   21.764318] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.810351] [drm] TV-20: set mode NTSC 480i 0
--
[   22.227215] i2c-adapter i2c-2: unable to read EDID block.
[   22.227218] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   22.231901] i2c-adapter i2c-2: unable to read EDID block.
[   22.231904] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   22.277924] [drm] TV-20: set mode NTSC 480i 0
--
[   32.037999] i2c-adapter i2c-2: unable to read EDID block.
[   32.038003] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.057102] i2c-adapter i2c-2: unable to read EDID block.
[   32.057106] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.103765] [drm] TV-20: set mode NTSC 480i 0
--
[   32.512754] i2c-adapter i2c-2: unable to read EDID block.
[   32.512760] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.517997] i2c-adapter i2c-2: unable to read EDID block.
[   32.518003] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.566732] [drm] TV-20: set mode NTSC 480i 0
--
[   32.957747] i2c-adapter i2c-2: unable to read EDID block.
[   32.957750] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.962432] i2c-adapter i2c-2: unable to read EDID block.
[   32.962434] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.008472] [drm] TV-20: set mode NTSC 480i 0
--
[   34.357105] i2c-adapter i2c-2: unable to read EDID block.
[   34.357108] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   34.361806] i2c-adapter i2c-2: unable to read EDID block.
[   34.361809] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   34.407856] [drm] TV-20: set mode NTSC 480i 0


```

---

### Post by lidex on 2010-04-06
Can you post the output of this command please?
```
cat /etc/modprobe.d/alsa-base.conf
```

I would suggest an alsa update at this point. You can click on the alsa-update script link in my sig.

---

### Post by tylerhughes on 2010-04-07
> **lidex said:**
> Can you post the output of this command please?
```
cat /etc/modprobe.d/alsa-base.conf
```



certainly :)

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=laptop enable=1 index=0


```

will do the alsa update asap. thanks for all your help!

---

### Post by tylerhughes on 2010-04-07
alsa update complete....still no change :/

---

### Post by lidex on 2010-04-07
> **tylerhughes said:**
> alsa update complete....still no change :/
Did you recheck alsamixer?

---

### Post by tylerhughes on 2010-04-09
> **lidex said:**
> Did you recheck alsamixer?

recheck??? how do you mean? sorry, im still a bit new to linux :guitar:

---

### Post by miegiel on 2010-04-09
> **tylerhughes said:**
> recheck??? how do you mean? sorry, im still a bit new to linux :guitar:

In a terminal (see applications menu) do :
```
alsamixer
```
controls:
[LIST]
[*]left/right arrows to select slider
[*]up/down to in/de-crease level
[*]Q/Z to in/de-crease left level
[*]E/C to in/de-crease right level
[*]M (un)mute
[*]F4 show outputs
[*]F5 show inputs
[*]F6 show all
[*]H help (I think)
[/LIST]

---

### Post by tylerhughes on 2010-04-09
okey dokey. version is 1.0.22.1 compiled on Feb 8 2010

---

### Post by miegiel on 2010-04-09
> **tylerhughes said:**
> okey dokey. version is 1.0.22.1 compiled on Feb 8 2010

Maybe I should let **lidex** speak for himself, I do get it wrong  sometimes when saying what I think someone means. But ... I think he means you sould check no sliders are all the way down or muted (|MM| below the slider).

---

### Post by lidex on 2010-04-09
> **miegiel said:**
> Maybe I should let **lidex** speak for himself, I do get it wrong  sometimes when saying what I think someone means. But ... I think he means you sould check no sliders are all the way down or muted (|MM| below the slider).

Right, I meant to check mixer levels again. alsa likes to reset the levels to zero.

---

### Post by tylerhughes on 2010-04-09
> **lidex said:**
> Right, I meant to check mixer levels again. alsa likes to reset the levels to zero.

ah, alright. none are zero or muted. but also there isnt separate mixers for speakers and headphones or anything like that....if theres supposed to be?

---

### Post by miegiel on 2010-04-09
> **tylerhughes said:**
> ah, alright. none are zero or muted. but also there isnt separate mixers for speakers and headphones or anything like that....if theres supposed to be?

There should be, well at least I have 1 for the laptop speakers and 1 for the headphones (see my alsamixer below). I have the same "soundcard" as you in a different laptop (acer timeline 3810T). However I'm not using ubuntu 9.10 (karmic), but testdriving the soon to be released 10.04 (lucid).

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                          F1:  Help               &#9474;
&#9474; Chip: Intel G45 DEVCTG                                   F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                 F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -19.00]                           Esc: Exit               &#9474;
&#9474;                                                                                  &#9474;
&#9474;   &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                &#9484;&#9472;&#9472;&#9488;   &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                &#9474;  &#9474;   &#9474;
&#9474;   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;   &#9474;
&#9474;   &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                       &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;   &#9474;
&#9474;   &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;   &#9474;
&#9474;    70    100<>100 100<>100 100<>100   0<>0                                0<>0   &#9474;
&#9474;< Master >Headphon Speaker    PCM    Front Mi  S/PDIF  S/PDIF D S/PDIF 1   Beep   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

---

### Post by tylerhughes on 2010-04-09
erg...this is all ive got
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Conexant CX20583 (Pebble HSF)                  F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5:[All]            F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -41.00, -41.00]               Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;                                         &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;OO&#9474;                                                  &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;             L    R                               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;                     CAPTURE  -------  -------  -------                       &#9474;
&#9474;    45<>45   99<>99                                                           &#9474;
&#9474;  < Master >  PCM     Mic B    Mic C    Mic E    Mic F    S/PDIF  S/PDIF D    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```
hopefully they will have this all sorted out when they release the 10.04?

---

### Post by miegiel on 2010-04-09
> **tylerhughes said:**
> erg...this is all ive got
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Conexant CX20583 (Pebble HSF)                  F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5:[All]            F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -41.00, -41.00]               Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;                                         &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;OO&#9474;                                                  &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;             L    R                               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;                     CAPTURE  -------  -------  -------                       &#9474;
&#9474;    45<>45   99<>99                                                           &#9474;
&#9474;  < Master >  PCM     Mic B    Mic C    Mic E    Mic F    S/PDIF  S/PDIF D    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```
hopefully they will have this all sorted out when they release the 10.04?

The column of > at the right edge of the window mean there are more sliders to the right outside the window. Hit the right arrow till you can't move to the right any further to make sure. ;)

Lucid is working great for me hardware wise, there are some general bugs, but most of the ones that where bugging me have been splat. It looks promising.

---

### Post by tylerhughes on 2010-04-09
> **miegiel said:**
> The column of > at the right edge of the window mean there are more sliders to the right outside the window. Hit the right arrow till you can't move to the right any further to make sure. ;)

Lucid is working great for me hardware wise, there are some general bugs, but most of the ones that where bugging me have been splat. It looks promising.

nope, just a "capture" and an "ext mic"

and sweet! do you happen to know an est timeframe for 10.04 to be made public?

---

### Post by miegiel on 2010-04-09
> **tylerhughes said:**
> nope, just a "capture" and an "ext mic"

and sweet! do you happen to know an est timeframe for 10.04 to be made public?

April 29th, usually on the very last hour of the day in global time (UTC) ± 2 hours.

---

### Post by bretteroo on 2010-04-09
I have this same issue with my HP G60 - 630us.  I have also done the above steps to no avail.

---

### Post by lidex on 2010-04-09
Try this for me. Open alsa-base.conf for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Comment out or remove this line:
```
options snd-hda-intel model=laptop enable=1 index=0
```
Add this line:
```
options snd-hda-intel model=dell-vostro
```
Save. Close. Reboot. Check alsamixer.

---

### Post by tylerhughes on 2010-04-10
> **lidex said:**
> Try this for me. Open alsa-base.conf for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Comment out or remove this line:
```
options snd-hda-intel model=laptop enable=1 index=0
```
Add this line:
```
options snd-hda-intel model=dell-vostro
```
Save. Close. Reboot. Check alsamixer.

woohooooooo! last night i upgraded to 10.04 and i just did this and it works perfectly!!!!!! the speakers mute themselves whenever i plug in the headphones!! thank you so much! :guitar:

---

### Post by miegiel on 2010-04-10
> **tylerhughes said:**
> woohooooooo! last night i upgraded to 10.04 and i just did this and it works perfectly!!!!!! the speakers mute themselves whenever i plug in the headphones!! thank you so much! :guitar:

Cool, but I must warn you that lucid is still being worked on and this can cause problems. And you being new to linux can make it difficult to pull your machine out of the mud when, for example, it gets stuck 1/2 way in the boot process after an update that inadvertently introduces a bug. That said, if you have the ubuntu CD you can always use that to boot (with "the try ubuntu without installing" option in the 1st menu) and go online to find out what you need to do to pull your machine out of the mud. But, fingers crossed, nothing bad will happen in the last 3 beta weeks. And if it does it will be a learning experience at least.
:lolflag:

---

### Post by peterroots on 2010-04-20
worked for me too but then I found it had killed the internal mic - reversing the changes did not restore the mic though so still looking for a solution!

---

### Post by miegiel on 2010-04-20
> **peterroots said:**
> worked for me too but then I found it had killed the internal mic - reversing the changes did not restore the mic though so still looking for a solution!

On my acer laptop I need to do [**this**]("http://ubuntuforums.org/showthread.php?p=9102538#post9102538") to use my internal mic. The disadvantage is that the external mic/input will also be unbalanced. I haven't tried, but I expect it will also affect recording from other sources.

---

