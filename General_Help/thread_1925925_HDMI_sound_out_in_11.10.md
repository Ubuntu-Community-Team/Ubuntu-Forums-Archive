---
title: "HDMI sound out in 11.10"
date: 2012-02-15
forum: General Help
---

### Post by drfreakynutz on 2012-02-15
I posted this in the mythbuntu forum, but I thought the general might help since it is a general issue as well.  I am simply trying to get any sound out of the hdmi out.

my hardware is:
MSI K9A2GM-FIH m-ATX motherboard socket AM2+ 780G chipset
Integrated ATI Radeon HD2300 Video with VGA and HDMI
AMD Sempron LE-1300 @ 2.3Ghz
HD5500 HDTV Tuner Card

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
~$ aplay -L
null
   Discard all samples (playback) or generate zero samples (capture)
pulse
   Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Front speakers
surround40:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Digital
   IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct sample mixing device
dmix:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct sample mixing device
dsnoop:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct sample snooping device
dsnoop:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct sample snooping device
hw:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct hardware device without any conversions
hw:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Hardware device with all software conversions
plughw:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
   HDA ATI HDMI, HDMI 0
   HDMI Audio Output
dmix:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct sample snooping device
hw:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Hardware device with all software conversions
```

```
$ lsmod | grep snd
snd_hda_codec_hdmi     31426  1 
snd_seq_midi           13132  0 
snd_hda_codec_realtek   254125  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80435  4 snd_hda_codec_hdmi,cx88_alsa,snd_hda_intel,snd_hda_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,cx88_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```

```
/proc/asound/card2$ more codec#0
Codec: ATI RS690/780 HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002791a
Subsystem Id: 0x00791a00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
```

I have tried to play wav files with:

```
aplay -D plughw:2,3 file.wav
```

and

```
mplayer file.wav -ao alsa:device=hw=2.3
```

also with subdevice 2,3,0.

I tried:

```
modprobe snd_hda_intel
```

and 

```
modprobe snd_hda_intel model=6stack-digout
```

I have no .asoundrc or /etc/asound.conf files currently.  I had installed pulseaudio and pavucontrol but removed them as I though they might complicate the issue. I haven't tried the speaker-test utility yet, but I'm not sure that is any different than getting aplay or mplayer to work.

Any help getting any kind of sound coming out of the hdmi port would be greatly appreciated.  thanks.

---

### Post by drfreakynutz on 2012-02-16
hate to bump my own thingy, but I'm still not getting anywhere with this.

---

### Post by Mark Phelps on 2012-02-16
Don't know if this will help ... but I'm running a PC under 11.10 and have an integraged AMD video chipset as well.

I'm not using the HDMI port, so I have sound set to the internal soundchip on the motherboard.

But, I believe there was an option to select the HDMI sound port associated with the integrated AMD chip.

You should check to see if you have the same options, and if so, and the HDMI port is not selected, see if you can select that.

---

### Post by drfreakynutz on 2012-02-16
sorry, where are you setting those options? I'm in xfce as I'm using mythbuntu, but I guess I can switch to gnome if necessary.

---

