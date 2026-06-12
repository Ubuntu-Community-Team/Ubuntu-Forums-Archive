---
title: "No Audio on Ubuntu With ALSA"
date: 2012-04-12
forum: General Help
---

### Post by MaximB on 2012-04-12
After having no luck with PulseAudio I decided to go back to ALSA, but now it also won't work.

When I run games from cli they give me no errors, but also no sound.
My music plays with VLC, but  cannot hear it.

I've checked the mixers and they aren't muted.
The conf files seems ok.
The devices are recognized as far as I can tell.

But I hear no sound.

Please help me.

If you need some conf files, please tell me.

---

### Post by raja.genupula on 2012-04-12
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by MaximB on 2012-04-12
Thanks,
I've tried everything in this link but I still here no sound.
The strange thing is that I don't get an error, and everything seems fine and running...
And yeah I've checked the the cables are connected ;)

---

### Post by hal8000 on 2012-04-12
You need to provide some hardware detail, sound card make . model and output from:

lspci -v | grep -i "audio"

lsmod | grep snd

If your sound modules are loaded and are in use (0 indicates not in use)
then it looks as though sound is working.

I had a problem with no sound once, turns out that my onboard graphics card had HDMI audio and sound was directed to that stream.

Check also that cables are fully connected, an easy test is to unplug cable from sound out and touch the jack with your finger a mains hum will be heard in your speakers.

---

### Post by MaximB on 2012-04-13
maximb@MaximB-HQ:~$ lspci -v | grep -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

maximb@MaximB-HQ:~$ lsmod | grep snd
snd_hrtimer            12744  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         118064  1 
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

---

