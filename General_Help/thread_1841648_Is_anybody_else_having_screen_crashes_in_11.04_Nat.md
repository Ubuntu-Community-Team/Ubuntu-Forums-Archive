---
title: "Is anybody else having screen crashes in 11.04 Natty Narwhal?"
date: 2011-09-09
forum: General Help
---

### Post by vidwarren on 2011-09-09
I'm on a Samsung NC10 Plus (netbook). Ubuntu 10.10 ran fine.

I upgraded to 11.04 around a month ago. Over the last week, I've run into a glitch a couple of times where the screen freezes:

- First it gets distorted and everything 'zig-zags'
- Then it goes black for a couple of seconds
- Then I can see a mixture of windows from everything I have open but I can't click on anything. Some parts seem 'blanked out' too.
- All I can do is shut the power off

The thing is, I can't see a pattern or reason for this happening. I think I'd just refreshed a page in my browser before it happening last time. I have also installed a fair bit of multimedia software recently including Cinelerra, Muse, Rosegarden and Qsynth. Not sure if they could have something to do with it.

Thanks in advance.

---

### Post by sum1nil on 2011-09-09
No and sorry but I'm on a cheap Emachine notebook and I never did hear tell of such things. 

My Natty runs smooth as <snip>

ATI Radeon 3200 with an AMD 64 TF-20.

I understand this post asked just if we were having screen crashes.

---

### Post by cottfcfan on 2011-09-10
I found that conflicting wireless modules was causing my screen to freeze.
Blacklisted all but one and runs smooth since.
Check whats  being loaded "lsmod".

---

### Post by vidwarren on 2011-09-10
Thanks for the reply.

It happened again before I saw this. I'm starting to worry that it could happen during updating.

This is what lsmod turned up. To be honest, I don't understand most of it:

```
vid@vid-N150P-N210P-N220P:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12680  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
wl                   2642531  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
binfmt_misc            13213  1 
lib80211               14570  1 wl
arc4                   12473  2 
i915                  451033  3 
snd_seq_midi           13132  0 
rfcomm                 38125  8 
joydev                 17322  0 
sco                    17827  2 
snd_rawmidi            25269  1 snd_seq_midi
brcm80211             690413  0 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  1 brcm80211
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
psmouse                73312  0 
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 brcm80211,mac80211
drm                   184164  4 i915,drm_kms_helper
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 

```

Also, I remembered when it just happened, the screen doesn't go black by itself, I just shut the lid on my laptop and opened it again to try to restart the monitor.

---

### Post by cottfcfan on 2011-09-10
Doesn't look to be anything untoward as far as I can see.
If you search the forums this seems to be a recurring problem that no one seems to be able to get to the bottom of.
Sorry I can't be of anymore help.

---

### Post by vidwarren on 2011-09-11
Thanks for taking the time all the same.

I'm starting to suspect that the problem has something to do with me  suspending the laptop. It has been fine since the last freeze and I've  noticed that it has only happened during a session in which I've  previously suspended by shutting the lid or where the laptop has  suspended itself when I've left it on and unplugged.

When I said that my laptop 'ran fine' on 10.10, I didn't mention that it  wouldn't wake up if I suspended/shut the lid (it 'ran fine' because I  just didn't  ever suspend it). This was a common problem on 10.10 so I  suspect there's a similar cause if lots of people are having the same  problem as me on 11.04.

---

