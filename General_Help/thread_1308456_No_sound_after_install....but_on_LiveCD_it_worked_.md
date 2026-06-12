---
title: "No sound after install....but on LiveCD it worked fine...Touchsmart TX2"
date: 2009-10-31
forum: General Help
---

### Post by Digikid on 2009-10-31
First off....here is my lsmod:

> Module                  Size  Used by
michael_mic             2204  4 
arc4                    1660  2 
ecb                     2524  2 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_si3054     4636  1 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               59080  0 
lib80211_crypt_tkip     8636  0 
x_tables               16544  1 ip_tables
fglrx                1989532  31 
videodev               36736  1 uvcvideo
snd_seq_dummy           2656  0 
psmouse                56180  0 
wl                   1272936  0 
lirc_ene0100            8096  0 
lp                      8964  0 
agpgart                34988  1 fglrx
lirc_dev               10804  1 lirc_ene0100
i2c_piix4               9932  0 
v4l1_compat            14496  2 uvcvideo,videodev
parport                35340  2 ppdev,lp
snd_seq_oss            28576  0 
serio_raw               5280  0 
joydev                 10272  0 
hid_ntrig               3740  0 
shpchp                 32272  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211                6432  2 lib80211_crypt_tkip,wl
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
usb_storage            52544  0 
r8169                  32064  0 
mii                     5212  1 r8169
video                  19380  0 
output                  2780  1 video


Laptop in question is a HP Touchsmart TX2 1224CA.  Yes I found that thread about the TX2Z and it did not work whatsoever.

Weird part is that the sound worked PERFECTLY when I was running off of the CD so why would it not work after the install?

I see that this is a widespread problem with HP and Linux......whats up with that?  LOL!!!

Again...please be _**POLITE and THROUGH**_....any rudeness will not be tolerated and reported.

---

### Post by Digikid on 2009-11-01
Anyone?

---

### Post by Digikid on 2009-11-06
Err...help would be MUCH appreciated.

---

