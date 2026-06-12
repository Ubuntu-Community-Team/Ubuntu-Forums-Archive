---
title: "Broken boot sequence after replacing an NVidia 6600GT with a Radeon X1300"
date: 2011-04-27
forum: General Help
---

### Post by Muadib25 on 2011-04-27
Greetings!

Yesterday, after my nVidia 6600GT left its last breath I had to revive somehow my Ubuntu box. So I used the next available card I had at my disposal, a Radeon X1300/1550 (RV516).

What I have done so far:

1. Using 2.6.35-48 generic (recovery) bootup, I managed to fire up the failsafeX.

2. I used this [**[COLOR="Blue"]guide[/COLOR]**]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to purge Nvidia leftovers.

3. I used this [**[COLOR="blue"]RadeonDriver guide[/COLOR]**]("https://help.ubuntu.com/community/RadeonDriver") to install the OpenSource Radeon driver.

When I try to boot using the normal choice on GRUB (kernel2.6.35-28-generic) , all I get is a console (no X).

Right now I am running X through Recovery boot, and my lsmod shows this:

```
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
snd_emu10k1_synth       5136  0 
snd_emux_synth         29012  1 snd_emu10k1_synth
snd_seq_virmidi         4193  1 snd_emux_synth
snd_seq_midi_emul       5547  1 snd_emux_synth
snd_intel8x0           25664  2 
snd_emu10k1           131818  3 snd_emu10k1_synth
snd_usb_audio          86480  1 
snd_ac97_codec         99227  2 snd_intel8x0,snd_emu10k1
ac97_bus                1014  1 snd_ac97_codec
snd_util_mem            3118  2 snd_emux_synth,snd_emu10k1
snd_pcm                71475  4 snd_intel8x0,snd_emu10k1,snd_usb_audio,snd_ac97_codec
snd_hwdep               5040  3 snd_emux_synth,snd_emu10k1,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
radeon                829223  3 
snd_rawmidi            17783  4 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6047  2 snd_seq_virmidi,snd_seq_midi
snd_seq                47174  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
joydev                  8767  0 
ttm                    56633  1 radeon
snd_timer              19067  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5744  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30200  1 radeon
usbhid                 36882  0 
uvcvideo               55847  0 
ppdev                   5556  0 
snd                    49038  23 snd_emux_synth,snd_seq_virmidi,snd_intel8x0,snd_emu10k1,snd_usb_audio,snd_ac97_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ns558                   3068  0 
emu10k1_gp              1472  0 
drm                   168060  4 radeon,ttm,drm_kms_helper
hid                    67742  1 usbhid
parport_pc             26058  1 
videodev               43098  1 uvcvideo
gameport                9327  4 ns558,emu10k1_gp
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26566  1 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_intel8x0,snd_emu10k1,snd_pcm
psmouse                59033  0 
i2c_algo_bit            5168  1 radeon
shpchp                 29886  0 
serio_raw               4022  0 
agpgart                32011  3 ttm,drm,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
floppy                 54311  0 
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
```


Here is also my Xorg.0.log: [[COLOR="Blue"]**http://pastebin.com/VkdQYp7p**[/COLOR]]("http://pastebin.com/VkdQYp7p")

Any help deeply appreciated!
Thanks in advance! :)
/Mua

---

### Post by Mark Phelps on 2011-04-28
Actually, since you're using the open-source drivers, if your Ubuntu is 10.x, you shouldn't need an Xorg file at all.

Suggest you rename it, reboot, and see if that helps.

---

### Post by Muadib25 on 2011-04-28
Strangely enough, everything works today, no Xorg.conf is present...plus I have also Direct Rendering!

How did U do that?  :P

Best Regards!
/Kle

---

