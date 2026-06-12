---
title: "Is my audio card 24bit?"
date: 2012-01-19
forum: General Help
---

### Post by ERRRIMMAD on 2012-01-19
Hello, how can I tell if my integrated audio card is 24bit or not, I'm using Ubuntu 11.10

---

### Post by ERRRIMMAD on 2012-01-20
bump

---

### Post by Rodney9 on 2012-01-20
Search google for the make and model, if you don't know install HardInfo.

> HardInfo is a small application that displays information about your
hardware and operating system. Currently it knows about PCI, ISA PnP, USB,
IDE, SCSI, Serial and parallel port devices.

Rodney

---

### Post by ERRRIMMAD on 2012-01-20
> **Rodney9 said:**
> Search google for the make and model, if you don't know install HardInfo.



Rodney

Thanks! =D I always try to figure this stuff out before I ask anyone but finding out the capabilities of sound devices is always frustrating, and trust me I looked for three days before I asked.

I assume my system is 24bit, but who knows, maybe HP skimped on my sound device.

Hardinfo (Cool app by the way! Thanks) says, intel corporation 82801 (ich10 family) hd controller. for audio device.

My system is a core two duo HP dx7500, and like most HP stuff they don't tell you squat about what the system is truly capable of, it was not my choice, LOL, I would rather just build my own system, but it was given to me, and, well, it's a free core two duo. XD

---

### Post by xyzzyman on 2012-01-20
You most likely don't actually have an intel sound card. It just shows that as your card is an onboard that falls under the 'Intel HDA Audio Codec' that replaced AC97. You most likely have a realtek or some other brand card.

The way to find out what you have is to run [AlsaInfo]("https://wiki.ubuntu.com/Audio/AlsaInfo"). Mine for example shows:

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Jan 16 02:36:49 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu precise (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 6930G     
Product Version:   Not Applicable


!!Kernel Information
!!------------------

Kernel release:    3.2.0-8-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


<snip>

!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0400000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


<snip>

!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x1025015e
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC888 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23

<snipped out the rest>


```

Once you scroll down to where it shows your actual audio chip, you'll see under the bits for everything it shows what it supports. Most likely it'll be 16, 20 & 24 as even the cheapest cards nowadays do. If you're comparing it to a dedicated sound card from say creative that does 24bit and you're looking to do high-end audio editing etc, there is a quality difference. If you're just listening to music and video don't worry about it. It's not that HP went "cheap", as the dx7500 is more of a business workstation desktop so that card is more than adequate. Modern onboard sound cards don't have the CPU hit that they used to a long time ago and I've been satisfied with them.

---

### Post by ERRRIMMAD on 2012-01-20
> **xyzzyman said:**
> You most likely don't actually have an intel sound card. It just shows that as your card is an onboard that falls under the 'Intel HDA Audio Codec' that replaced AC97. You most likely have a realtek or some other brand card.

The way to find out what you have is to run [AlsaInfo]("https://wiki.ubuntu.com/Audio/AlsaInfo"). Mine for example shows:

```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Jan 16 02:36:49 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu precise (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 6930G     
Product Version:   Not Applicable


!!Kernel Information
!!------------------

Kernel release:    3.2.0-8-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


<snip>

!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0400000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


<snip>

!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x1025015e
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC888 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23

<snipped out the rest>


```Once you scroll down to where it shows your actual audio chip, you'll see under the bits for everything it shows what it supports. Most likely it'll be 16, 20 & 24 as even the cheapest cards nowadays do. If you're comparing it to a dedicated sound card from say creative that does 24bit and you're looking to do high-end audio editing etc, there is a quality difference. If you're just listening to music and video don't worry about it. It's not that HP went "cheap", as the dx7500 is more of a business workstation desktop so that card is more than adequate. Modern onboard sound cards don't have the CPU hit that they used to a long time ago and I've been satisfied with them.

Yeah, I think you're correct, I believe I saw a realtek chip on the motherboard. =D

I have another computer I use for audio related apps, still, this computer is running Ubuntu Studio and if I want to mess with the apps I thought it would be nice to know if it truly has 24bit capabilities, anyways I followed your advice and found out it does. =D

I don't want to install another sound card on this system as Ubuntu and multiple sound cards have always been more of a headache than benefit to me.

Thanks for your help! my question has been answered, I wish Ubuntu would make FAQ guides about technical questions like the one you just answered for me and not about how to use Ubuntu one and other nonsense, although I do like Ubuntu one, LOL.

---

