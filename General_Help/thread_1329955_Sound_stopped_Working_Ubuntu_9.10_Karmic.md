---
title: "Sound stopped Working Ubuntu 9.10 Karmic"
date: 2009-11-17
forum: General Help
---

### Post by Gillimaster on 2009-11-17
Hello everyone,

I currently decided to use Ubuntu on my other laptop. Audio was working on it before I installed software (all of my software: flash, songbird, vlc player, eclipse IDE, etc). Im not exactly sure when it stopped. When I use a live cd it works fine. My computer is a HP TX2Z. I have not installed the touchscreen drivers. I am running Karmic. This was a direct fresh install (wasn't updated).

:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

:~$ lsmod | grep snd
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  3 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm

I have searched forums and have come to no solution. Any help would be greatly appreciated.

Thanks

---

### Post by Gillimaster on 2009-11-18
Well after further investigation I found out that my modem software was causing the problem. I used this link to troubleshoot [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

This part helped the most 

"In the volume control applet, PulseAudio lists a dummy/null sink.

Open a terminal and enter this command:

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

If you see something else than "pulseaudio" in the rightmost column, such as "slmodemd" or "timidity", you're affected.
"

I hope this can help someone with a similar problem.

---

### Post by cristoslc on 2009-11-21
I had the same problem on my HP touchSmart tx2z. I was able to resolve it by going to System > Administration > Hardware Drivers and deactivating the "Software modem" device.

This was after I had already added the "options snd-intel-hda model=toshiba" line to the bottom of my "/etc/modprobe.d/alsa-base.conf" configuration file.

This is acceptable for me because I do not use the modem, and it was simpler than modifying configurations as indicated in the links that [Gillimaster]("http://www.uluga.ubuntuforums.org/member.php?u=456975")_ _provided. If you do need the use of your modem, you may need to look through the more advanced configuration information to resolve your issue.

---

### Post by eli555 on 2009-11-23
try this [URL="https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/486808"]https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/486808
[/URL]

---

### Post by code_linux on 2009-12-26
@cristoslc

Sound problem here too. Deactivated the software modem as described and sound is back.
Thanks!

---

