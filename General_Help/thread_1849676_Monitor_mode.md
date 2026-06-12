---
title: "Monitor mode"
date: 2011-09-25
forum: General Help
---

### Post by freefixkorma on 2011-09-25
hi guys i am running on ubuntu 10.04 on 64bit acer aspire 5742,i am trying to place my wireless card on monitor mode but i cant ,is there any good guide and how to i will appreciate that thanks in advnace sorry i forgot to place info of controller Broadcom Corporation NetLink BCM57780 thanks in advance

freefix

---

### Post by bkratz on 2011-09-25
> **freefixkorma said:**
> hi guys i am running on ubuntu 10.04 on 64bit acer aspire 5742,i am trying to place my wireless card on monitor mode but i cant ,is there any good guide and how to i will appreciate that thanks in advnace sorry i forgot to place info of controller Broadcom Corporation NetLink BCM57780 thanks in advance

freefix


The Broadcom BCM57780 is you ethernet card (wired) connection; not your wireless card. Please either specify it or post theoutput to the following terminal commands:

```
lspci -nn | grep 0280
lsmod
iwconfig

```
The first should show the wireless card,  and the second all the modules used.

---

### Post by freefixkorma on 2011-09-25
thanks for the reply this is output from the command line that you gave me thanks for reply and i am sorry for any ignorance on my previous posted

freefix:p





02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)


korma@korma:~$ lsmod
Module                  Size  Used by
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203376  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
ppdev                   5259  0 
snd_hda_intel          22165  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289443  3 
drm_kms_helper         29361  1 i915
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
lib80211_crypt_tkip     7596  0 
drm                   163066  4 i915,drm_kms_helper
serio_raw               3978  0 
uvcvideo               57406  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
led_class               2864  0 
soundcore               6620  1 snd
intel_agp              24671  2 i915
i2c_algo_bit            5028  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  2 drm,intel_agp
wl                   1959630  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39873  0 
tg3                   109580  0 
ahci                   32392  2 


korma@korma:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:1  Signal level:170  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by Dangertux on 2011-09-25
In your case (if your card supports it)

The following would probably work

```

sudo iwconfig eth1 mode monitor

```

---

### Post by freefixkorma on 2011-09-25
thanks for the reply this is the output from the comman thanks for your time

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

---

### Post by bkratz on 2011-09-25
> **freefixkorma said:**
> hi guys i am running on ubuntu 10.04 on 64bit acer aspire 5742,i am trying to place my wireless card on monitor mode but i cant ,is there any good guide and how to i will appreciate that thanks in advnace sorry i forgot to place info of controller Broadcom Corporation NetLink BCM57780 thanks in advance

freefix



There are two drivers that support your card: the Broadcom STA (the one you use called wl) and the new brcm80211 driver.  The STA being proprietary does not support monitor mode, and the other is working to get there--but I don't believe it supports it yet either...sorry.

---

### Post by freefixkorma on 2011-09-25
thanks for the reply someday someone will come up case close than for me

freefix:D

---

