---
title: "Ubuntu 11.10 colours"
date: 2012-02-24
forum: General Help
---

### Post by Veerdavid on 2012-02-24
Hi everyone.
I've installed Ubuntu 11.10 recently on an MSI notebook with win7 on another partition.
My problem is that some colours are displayed differently as they should be.
For example, here blue turned into pink

Any ideas what could cause this and how to solve it?
[IMG]http://ubuntuforums.org/home/david/Asztal/pink.png[/IMG]

---

### Post by idonthaverabbies on 2012-02-24
have you tried other themes?

---

### Post by Veerdavid on 2012-02-24
Yes, the original one. It was the same.

---

### Post by idonthaverabbies on 2012-02-24
weird i am no expert but id guess a video card driver issue.but ya probably will be better waiting for some one with more knowledge then me

---

### Post by Veerdavid on 2012-02-27
bump
btw I forgot to mention that other programs' colour does the same too

---

### Post by josephmills on 2012-02-27
I have seen this happen before with one of my clients boxs.Not sure if it is the same thing but.  

could you please open your terminal(ctrl+alt+t)
then enter in 
```
lspci -nn | grep VGA
```
then 
```
lsmod
```

then paste that all here

---

### Post by Veerdavid on 2012-02-27
harased@harased:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] [1002:9552]
harased@harased:~$ lsmod
Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
cryptd                 19801  0 
aes_i586               16956  3 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
vesafb                 13449  1 
rt2860sta             494649  0 
arc4                   12473  2 
rt2800pci              18119  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec_realtek   255882  1 
fglrx                2434640  202 
snd_hda_intel          28209  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
psmouse                59039  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sis_agp                13127  0 
serio_raw              12990  0 
soundcore              12600  1 snd
eeprom_93cx6           12653  1 rt2800pci
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sis190                 22622  0 
sata_sis               12704  2

---

### Post by josephmills on 2012-02-27
Sorry not the same thing his was nvidia card and he had the wrong driver installed. Sorry to waste your time.

---

### Post by Veerdavid on 2012-02-27
I see, thanks anyway ((:

---

### Post by Veerdavid on 2012-02-29
I removed the closed driver (not sure what it is called i english) for the video card and that solved the problem... strange

---

