---
title: "No sound though card appears to be working"
date: 2011-03-11
forum: General Help
---

### Post by supradave on 2011-03-11
Yesterday, I nuked my motherboard's built-in sound though some static discharge.  I went and purchased an Asus Xonar DG.  It appears to be working just fine.  And no, it's not muted in the alsamixer or other program, AFAICT.  Which is why I'm leaning to that it's muted (and I'm plugged in to the green hole on the card and have tried the black and blue as well, and I do get some noise when plugging into the red hole (microphone)).

```
lsmod | grep snd
snd_oxygen             14145  3 
snd_oxygen_lib         30951  1 snd_oxygen
snd_pcm                71314  2 snd_oxygen_lib
snd_page_alloc          7120  1 snd_pcm
snd_mpu401_uart         5853  1 snd_oxygen_lib
snd_seq_midi            4716  0 
snd_rawmidi            17932  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47537  2 snd_seq_midi,snd_seq_midi_event
snd_timer              18657  2 snd_pcm,snd_seq
snd_seq_device          6064  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    51204  14 snd_oxygen,snd_oxygen_lib,snd_pcm,snd_mpu401_uart,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DG [Xonar DG], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DG [Xonar DG], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
cat /proc/asound/cards 
 0 [DG             ]: CMI8786 - Xonar DG
                      C-Media Oxygen HD Audio at 0xd000, irq 20
```

For example, mplayer appears to be working in that it looks like it's working and it plays video.  Just no sound.

In playing with the alsamixer, I was able to get a pop through when I changed the analog output from speakers to headphones.
```
amixer -c 0
Simple mixer control 'Headphones Impedance',0
  Capabilities: penum
  Items: '< 64 ohms' '64-150 ohms' '150-300 ohms'
  Item0: '< 64 ohms'
Simple mixer control 'Front Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture -24 - 24
  Front Left: Capture 24 [100%] [off]
  Front Right: Capture 24 [100%] [off]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture -24 - 24
  Front Left: Capture -24 [0%] [off]
  Front Right: Capture -24 [0%] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture -24 - 24
  Front Left: Capture -24 [0%] [on]
  Front Right: Capture -24 [0%] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture -24 - 24
  Front Left: Capture -24 [0%] [off]
  Front Right: Capture -24 [0%] [off]
Simple mixer control 'ADC High-pass Filter',0
  Capabilities: cenum
  Items: 'Active' 'Frozen'
  Item0: 'Active'
Simple mixer control 'Analog Input Monitor',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 1
  Mono: Playback 1 [100%] [0.00dB] [off]
Simple mixer control 'Analog Output',0
  Capabilities: penum
  Items: 'Speakers' 'Headphones' 'FP Headphones'
  Item0: 'Speakers'
Simple mixer control 'Stereo Upmixing',0
  Capabilities: enum
  Items: 'Front' 'Front+Surround'
  Item0: 'Front+Surround'
```

---

