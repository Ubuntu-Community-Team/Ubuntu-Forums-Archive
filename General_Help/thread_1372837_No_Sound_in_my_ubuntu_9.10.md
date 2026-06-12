---
title: "No Sound in my ubuntu 9.10"
date: 2010-01-05
forum: General Help
---

### Post by yinglcs2 on 2010-01-05
HI,

I am running ubuntu 9.10. But there is no sound in my environment.
When I go to System->Preference, there is no 'sound' entry there.

And when I do 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ asoundconf list
asoundconf: command not found

Please tell me how can I fix my problem?

Thank you.

---

### Post by MichealH on 2010-01-05
Could you post the output of **lspci **(thats a L not a 1) and **lsmod **(again a L not a 1)

---

### Post by yinglcs2 on 2010-01-05
Thanks for your help.

Here are the output:

~:986:1$ lsmod
Module                  Size  Used by
usb_storage            52576  3 
binfmt_misc             8356  1 
vboxvfs                34620  0 
vboxvideo               1884  1 
drm                   159584  2 vboxvideo
agpgart                34988  1 drm
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6432  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ppdev                   6688  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               9932  0 
parport_pc             31940  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
vboxguest             143836  7 vboxvfs
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
pcnet32                32644  0 
mii                     5212  1 pcnet32
floppy                 54916  0 
~:987:2$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
~:988:3$

---

