---
title: "Problems with WUSB600N in 11.10"
date: 2011-10-28
forum: General Help
---

### Post by Cpierce on 2011-10-28
I just upgraded to 11.10 from 10.04 and my linksys wusb600n v1 stopped working. It sees my wifi, but won't connect. I read thru the forums and tried blacklisting rt2800usb, tried sudo modprobe rt2800usb, tried shutting down and unplugging the adaptor, powering up and then plugging the adaptor back in. I looked up the correct driver which is rt2870, but sudo modprobe rt2870 can't find anything. I have a duel boot and the adaptor works fine with windows so I know it is good. Wifi works on the other computers in the house so I know it is fine. Here is my "lsmod":

chuck@chuck-computer:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  8 rfcomm,bnep
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
radeon                925020  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 radeon
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
uas                    17699  0 
sis900                 22729  0 
chuck@chuck-computer:~$ 


Can someone help please ?

---

### Post by Cpierce on 2011-10-29
I gave up and just installed ndiswrapper. Not a "real" solution, but I got it working.

---

