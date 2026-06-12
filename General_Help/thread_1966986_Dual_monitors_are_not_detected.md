---
title: "Dual monitors are not detected"
date: 2012-04-27
forum: General Help
---

### Post by Houmie on 2012-04-27
Hi,

I have just started Ubuntu 12.04 64Bit from a USb stick.  

I have two 24" dell monitors. One is connected to i5 internal intel graphic card (the one that is now working).

The main screen is connected through display port to an ATI Radeon HD 6570.

During bootup the screen with the ATI card showed up something, but once the boot was finished, I can now only see the screen connected to the internal Intel graphic card.

What do I have to do to run them both in unison like an extended desktop as its possible in Windows7?

Many Thanks,
Houman

---

### Post by josephmills on 2012-04-27
I dont care what is possible in windows as this is not windows but lets take a lookie-lue shall we. 

please open terminal and enter in
```
lspci | grep VGA 
```
also 
```
dmesg
```
```
lsmod
```
Then paste that all here 
TAKE OUT IPADRESS and MAC ADDRESS if you like.

---

### Post by Houmie on 2012-04-27
Thanks for your help:

1)

[HTML]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6570][/HTML]

2) ...

3)

[HTML]Module                  Size  Used by
nls_utf8               12557  1 
udf                    94317  1 
crc_itu_t              12707  1 udf
dm_crypt               23125  0 
snd_hda_codec_hdmi     32474  2 
snd_hda_codec_realtek   223867  1 
snd_usb_audio         122982  2 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
parport_pc             32866  1 
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
ppdev                  17113  0 
rfcomm                 47604  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
psmouse                87603  0 
dcdbas                 14490  0 
mei                    41616  0 
snd_timer              29990  2 snd_seq,snd_pcm
lp                     17799  0 
bnep                   18281  2 
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
parport                46562  3 parport_pc,ppdev,lp
snd                    78855  26 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
bluetooth             180104  10 rfcomm,bnep
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dm_multipath           23230  0 
mac_hid                 
soundcore              15091  1 snd
squashfs               36799  1 
overlayfs              28305  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 652957  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
uas                    18027  0 
usb_storage            49198  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
radeon                804372  0 
i915                  468651  3 
e1000e                156693  0 
video                  19596  1 i915
ttm                    76949  1 radeon
drm_kms_helper         46978  2 radeon,i915
drm                   242038  6 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
[/HTML]

---

### Post by josephmills on 2012-04-27
gezz everything is looking good for me. 

...

go to the power button and then displays are they both showing up ? 
can you take a screen shot of that ? 

thanks

---

### Post by Houmie on 2012-04-27
Sure here it is:

[IMG]http://i.imgur.com/Qxro7.png[/IMG]

Thanks

---

### Post by josephmills on 2012-04-27
press the detect display then turn down resolution 
turn that one off play with it and see if you can get it to show up
:) besides that I am at a loss. 

sorry

---

### Post by Houmie on 2012-04-28
Can Ubuntu use two separate graphic cards at all? 
Or do the two monitors have to be connected to the same graphic card?

Thanks

---

### Post by Houmie on 2012-04-28
I don't understand apparently multi-monitors are meant to be improved in Ubuntu:

[http://design.canonical.com/2011/12/improving-the-multi-monitor-experience-in-ubuntu/](http://design.canonical.com/2011/12/improving-the-multi-monitor-experience-in-ubuntu/)

How comes I can't get two graphic cards to work on my system with only two monitors?

Can anyone confirm, that Ubuntu actually supports two graphic cards on one PC?

---

### Post by elapouya on 2012-04-28
I do have the same problem :

Ubuntu 12.04 LTS + Desktop PC with Nvidia GTX 470 + 2x 1920x1200 pixels HP monitors :

without NVIDIA drivers : both monitors are detected, no problem, but not accelerated.
with official ubuntu NVidia drivers : only one monitor detected, seen as a "laptop screen".

```
elapouya@pcubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF100 [GeForce GTX 470] (rev a3)
elapouya@pcubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40257  1 
vesafb                 13844  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  4 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_usb_audio         122982  1 
snd_usbmidi_lib        25395  1 snd_usb_audio
nvidia              12319264  40 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
mxm_wmi                12979  0 
snd_seq_midi           13324  0 
ppdev                  17113  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath5k                 156407  0 
ath                    24067  1 ath5k
wmi                    19256  1 mxm_wmi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  1 ath5k
parport_pc             32866  1 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  3 ath5k,ath,mac80211
snd                    78855  24 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_logitech_dj        18593  0 
pwc                    83725  0 
videobuf2_core         33065  1 pwc
videodev               98259  1 pwc
mac_hid                13253  0 
v4l2_compat_ioctl32    17128  1 videodev
videobuf2_vmalloc      12832  1 pwc
videobuf2_memops       13230  1 videobuf2_vmalloc
i7core_edac            28102  0 
serio_raw              13211  0 
edac_core              53746  3 i7core_edac
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
pata_it8213            13079  0 
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
pata_jmicron           12747  0 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
```

---

### Post by elapouya on 2012-04-28
I just ran 'nvidia-settings' to activate the 2nd monitor. :)

---

### Post by Janiporo on 2012-04-28
Same problem, and multiple others. While you guys sort this out, I am going to use my 10.04 ^_^

Sometimes I got picture to second monitor, it was grey and only X-cursor there.

Yayy.

---

### Post by Houmie on 2012-04-29
> **elapouya said:**
> I just ran 'nvidia-settings' to activate the 2nd monitor. :)

I am happy for you. Is there any equivalent command for ATI?
Anyone?

---

### Post by carranty on 2012-04-29
> **Janiporo said:**
> Same problem, and multiple others. While you guys sort this out, I am going to use my 10.04 ^_^

Sometimes I got picture to second monitor, it was grey and only X-cursor there.

Yayy.
  Follow elapouya's advice.  With an Nvidia card you can run 

```
gksu nvidia-settings 
```

from the terminal.  You should then be able to set up the two monitors.  I find the same problem (with the grey screen) if I try to set up two separate x-screens, but twinview works fine.

@ Houmie, I'm sorry, I don't know the equivalent command for ATI cards but I believe the equivalent program is ATI Catalyst Control Center, hopefully you can find it using the dash -- I suspect you'll need to activate the ATI proprietary driver before this will function.

---

### Post by WebbyIT on 2012-05-01
> **carranty said:**
> Follow elapouya's advice.  With an Nvidia card you can run 

```
gksu nvidia-settings 
```

from the terminal.  You should then be able to set up the two monitors.  I find the same problem (with the grey screen) if I try to set up two separate x-screens, but twinview works fine.


[s]I have a gtx470 with two monitors, but if I active twinview it doesn't works well, around global menu i have white space, and it isn't fluid...[/s]
I solved using nouveu

---

