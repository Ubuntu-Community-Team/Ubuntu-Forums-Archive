---
title: "Help troubleshooting suspend"
date: 2009-09-25
forum: General Help
---

### Post by Brutus123 on 2009-09-25
Hi!

I recently bought an ASRock Ion 330 and installed [XBMCBuntu]("http://xbmc.org/wiki/?title=XBMCbuntu") (Minimal Ubuntu + xbmc) on it.
Everything ran fine (and suspend was working) until I added a Hauppauge WinTV PVR USB2 (external TV-card).
The TV-card itself seems to work fine as far as I have tested yet (the bundled remote is working and the tv-card is producing output 

althought I havent tuned it yet so I'm only seeing noice at the moment).
After adding this TV-card to the mix suspend and hibernate stopped working, trying to do a suspend will now result in a black screen with 

a lone cursor blinking in the upper right corner, the keyboard is not responding and I cannot SSH to it from another computer.
If I remove the TV-card suspend works fine again.

Since I have next to no Linux experience I don't really know where to begin..

I've had a look at the /var/log/pm-suspend.log, but I didn't find anything strange (probably due to my limited knowledge):
```
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Sep 25 14:04:19 CEST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux XBMC 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
cx8800                 38148  0 
cx88xx                 79272  1 cx8800
videobuf_dvb           15236  1 cx88xx
ivtv                  150340  0 
bttv                  171924  0 
ir_common              52228  2 cx88xx,bttv
compat_ioctl32          9344  3 cx8800,ivtv,bttv
i2c_algo_bit           14084  3 cx88xx,ivtv,bttv
videobuf_dma_sg        20484  3 cx8800,cx88xx,bttv
videobuf_core          26500  5 cx8800,cx88xx,videobuf_dvb,bttv,videobuf_dma_sg
btcx_risc              13064  3 cx8800,cx88xx,bttv
lirc_i2c               17028  1 
lirc_dev               19892  1 lirc_i2c
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
parport                42220  1 lp
tuner_simple           22544  1 
tuner_types            22400  1 tuner_simple
tda9887                18564  1 
tda8290                20740  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
tuner                  32836  0 
saa7115                24496  0 
msp3400                38732  0 
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
pvrusb2               146008  0 
nvidia               9594760  36 
snd_seq_dummy          10756  0 
dvb_core               92032  2 videobuf_dvb,pvrusb2
snd_seq_oss            37760  0 
agpgart                42696  1 nvidia
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx2341x                20996  2 ivtv,pvrusb2
snd_timer              29704  3 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            20992  8 cx8800,ivtv,bttv,tuner,saa7115,msp3400,pvrusb2,cx2341x
videodev               41600  7 cx8800,cx88xx,ivtv,bttv,tuner,msp3400,pvrusb2
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
v4l1_compat            21764  2 pvrusb2,videodev
shpchp                 40212  0 
forcedeth              61712  0 
soundcore              15200  1 snd
pcspkr                 10496  0 
serio_raw              13444  0 
tveeprom               20100  4 cx88xx,ivtv,bttv,pvrusb2
usbhid                 42336  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       1543900     248844    1295056          0       6236     122616
-/+ buffers/cache:     119992    1423908
Swap:      3903784          0    3903784
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Fri Sep 25 14:04:20 CEST 2009: performing suspend

```

Any help on how to troubleshoot this further will be greatly appreciated.

---

