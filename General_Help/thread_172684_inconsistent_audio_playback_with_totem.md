---
title: "inconsistent audio playback with totem"
date: 2006-05-09
forum: General Help
---

### Post by narboo on 2006-05-09
Hi,

3rd day on Linux.

I'm getting inconsistent audio playback when using the Totem Movie Player.  I'm guessing it's a plug-in issue but haven't been able to resolve it.  I've installed totem and totem-xine.

My audio player is:
sudo lspci | grep -i audio
0000:00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

lsmod | grep snd
snd_cmipci             30368  3
gameport               14472  1 snd_cmipci
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10120  1 snd_pcm
snd_opl3_lib            9856  1 snd_cmipci
snd_timer              21764  2 snd_pcm,snd_opl3_lib
snd_hwdep               8608  1 snd_opl3_lib
snd_mpu401_uart         6784  1 snd_cmipci
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  2 snd_opl3_lib,snd_rawmidi
snd                    48644  16 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd

cat /proc/asound/cards
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xd000, irq 11

Appreciate any help.

Thx.
-Rich

---

