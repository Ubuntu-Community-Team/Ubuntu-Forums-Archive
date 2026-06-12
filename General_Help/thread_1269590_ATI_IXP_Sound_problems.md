---
title: "ATI IXP Sound problems"
date: 2009-09-18
forum: General Help
---

### Post by csi_guy on 2009-09-18
I am having problems getting my sound to work on my PC.  I have been at it for a couple days now with no real headway, ( I was able to make the startup sound for login but no more.  I have checked to make sure that sound is not muted and that the volume is not off.  
I have gone through the sound trouble shooting guide at < [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) >   I am attaching system info hoping for some resolution :)  Thanks in advance and sorry for the long drawn out post. 

Here is a link to my alsa-info.sh .  This is all my sound info.
[http://www.alsa-project.org/db/?f=a76233b8c06c7817e7c6764fb78b625dd7f95fd6](http://www.alsa-project.org/db/?f=a76233b8c06c7817e7c6764fb78b625dd7f95fd6)

-Examiner:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Examiner:~$ sudo lspci -v | grep AC   

[sudo] password for *******: 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Kernel driver in use: ATI IXP AC97 controller



Examiner:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
snd_atiixp             24204  3 
snd_ac97_codec        112292  1 snd_atiixp
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12416  0 
ati_agp                14988  0 
agpgart                42696  1 ati_agp
ppdev                  15620  0 
snd                    62628  16 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_atiixp,snd_pcm
pcspkr                 10496  0 
i2c_piix4              18448  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usb_storage            82880  1 
reiserfs              236288  1 
usbhid                 42336  0 
ohci1394               38576  0 
8139too                32128  0 
ieee1394               94660  1 ohci1394
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by csi_guy on 2009-09-18
I have tried editing my alsa conf file with the suggestions from the sound troubleshooting document.  

I am starting to think that another OS might be the solution here....

Thanks


update:
Still working on it with no luck.  I see that this is affecting many distros, SUSE, Fedora, Mandriva.  I have tried installing other distros hoping that it would just work.(BT3, BT4 beta & pre-final, Debian, PCLinuxOS and Ubuntu 7 ( No such luc)k, but will keep trying and post the solution here when I finally figure it out.

---

### Post by csi_guy on 2009-09-19
Bump :)

---

