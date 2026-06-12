---
title: "Ubuntu 10.04 LTS Compaq Presario V6000 Wi-fi"
date: 2011-09-17
forum: General Help
---

### Post by SipSomeSalt on 2011-09-17
I currently did a fresh install of Ubuntu 10.04 on it's own partition on my Compaq V6000. There is only ONE problem so far -- my WI-FI!!!

When I ran lshw -C network it said my wireless is DISABLED I installed b43 and still nothing. I just don't know what to do, guys. 

Can you help me?

---

### Post by SipSomeSalt on 2011-09-17
```

dean@WalterMcIntosh:~$ lsmod Module                  Size  Used by binfmt_misc             6587  1  ppdev                   5259  0  joydev                  8740  0  snd_hda_codec_conexant    22705  1  fbcon                  35102  71  tileblit                1999  1 fbcon font                    7557  1 fbcon bitblit                 4707  1 fbcon softcursor              1189  1 bitblit vga16fb                11385  0  vgastate                8961  1 vga16fb snd_hda_intel          22069  2  snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel snd_hwdep               5412  1 snd_hda_codec snd_pcm_oss            35308  0  snd_mixer_oss          13746  1 snd_pcm_oss snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss snd_seq_dummy           1338  0  arc4                    1153  2  snd_seq_oss            26722  0  snd_seq_midi            4557  0  snd_rawmidi            19056  1 snd_seq_midi snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event snd_timer              19098  2 snd_pcm,snd_seq snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq i915                  288611  3  b43                   163556  0  drm_kms_helper         29329  1 i915 mac80211              205402  1 b43 snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device drm                   162377  4 i915,drm_kms_helper intel_agp              24375  2 i915 cfg80211              126144  2 b43,mac80211 led_class               2864  1 b43 soundcore               6620  1 snd psmouse                63677  0 serio_raw               3978  0  i2c_algo_bit            5028  1 i915 agpgart                31724  2 drm,intel_agp snd_page_alloc          7076  2 snd_hda_intel,snd_pcm video                  17375  1 i915 output                  1871  1 video lp                      7028  0  parport                32635  2 ppdev,lp e100                   28211  0  mii                     4381  1 e100 ahci                   32360  2  ssb                    38934  1 b43

```

```

dean@WalterMcIntosh:~$ ifconfig eth0      Link encap:Ethernet  HWaddr 00:16:36:bc:b6:56             UP BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:76 errors:0 dropped:0 overruns:0 frame:0           TX packets:76 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

```

```

dean@WalterMcIntosh:~$ iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     IEEE 802.11bg  ESSID:off/any             Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off

```

---

### Post by bkratz on 2011-09-18
One more (at least for now) thing to post would be 

rfkill list all

so we can see if there is a hard or soft block.

---

### Post by SipSomeSalt on 2011-09-21
Yo -- I solved it. Um...I used one of the Ubuntu walkthroughs for Broadcom users without internet service. It worked.

---

### Post by bkratz on 2011-09-21
> **SipSomeSalt said:**
> Yo -- I solved it. Um...I used one of the Ubuntu walkthroughs for Broadcom users without internet service. It worked.


Well, glad to hear you got it going, enjoy!

---

