---
title: "ubuntu 10.04 no sound and can't detect wireless"
date: 2011-08-20
forum: General Help
---

### Post by edward091810 on 2011-08-20
hi i'm sorry for being a noob but, i should ask this to get information straight to the point. i installed a ubuntu 10.04 netbook edition side by side with windows 7 professional on my netbook [COLOR="Red"]hp mini 110-3000 ee pc[/COLOR], ubuntu loaded very fine but the problem is after downloading all the required software and install everything ubuntu cannot detect wireless, (whereas windows 7 can detect) and even if i installed all needed plug-ins i still can't hear any sound tying to play mp3 or in youtube. anyone would like to help me i tried browsing the forums but none of it gave a best answer. thank you in advance... :confused:

---

### Post by Docaltmed on 2011-08-20
First, click on the speaker icon in the bar at the top of the screen and make sure the speakers aren't muted. Also, click on "sound preferences" on that same menu, and ensure that nothing is muted there. I know, it sounds silly, but more than one of us [ahem] has been caught by that.

Wireless is a world unto itself, but you might try going to the system menu and clicking on "additional drivers." (Be connected by ethernet when you do this). I've had a couple of computers that needed to use proprietary drivers to get wireless working, which were not downloaded in the initial installation.

---

### Post by cottfcfan on 2011-08-20
To help with wireless we need to know what module is being used.
Open up a terminal and post the output of:
```
lsmod
```

---

### Post by edward091810 on 2011-08-20
> **cottfcfan said:**
> To help with wireless we need to know what module is being used.
Open up a terminal and post the output of:
```
lsmod
```



edwardbriones@edwardbriones-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_hwdep               5412  1 snd_hda_codec
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm_oss            35308  0 
vga16fb                11385  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  4 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  5 i915,drm_kms_helper
videodev               34361  1 uvcvideo
soundcore               6620  1 snd
rt3090sta             674216  0 
lp                      7028  0 
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
video                  17375  1 i915
psmouse                63677  0 
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
serio_raw               3978  0 
joydev                  8740  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169

---

### Post by cottfcfan on 2011-08-20
Looks like your using the same chipset as me rt3090sta.
Following post 1 in the following thread very carefully, worked perfectly for me.
[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by edward091810 on 2011-08-20
i manage to solve the issue by downloading rt3090 .deb and installing it after reboot it instantly got connected..

---

### Post by edward091810 on 2011-08-20
> **cottfcfan said:**
> Looks like your using the same chipset as me rt3090sta.
Following post 1 in the following thread very carefully, worked perfectly for me.
[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

thanks my good friend one last question regarding my sound i still cant hear any and finaly how can we customize the home.

---

### Post by cottfcfan on 2011-08-21
Have you tried the suggestion in post 2? Thats a common problem.

---

### Post by edward091810 on 2011-08-21
> **cottfcfan said:**
> Have you tried the suggestion in post 2? Thats a common problem.

nope i just tried to locate my wifi card and found that it was not been installed yet. then browsed for the thread related to rt3090 then found the right thread read a little and go to a new tab and download a rt3090 for ubuntu, the first one i actually downloaded was an exe file. then tried the second time and i now downloaded .deb file. then i try unpacking it and install then after a reboot. wifi in now recognized. thanks anyway for your help.

---

### Post by cottfcfan on 2011-08-21
Did you follow the thread in post 5 exactly?
I know you have the rt3090 chipset, but the rt2860sta in that thread is exactly the same. If you follow it through it should work perfectly.
Be careful with trying other things, as they may well cause a module conflict, and you could end up needing to reinstall.
If you have it working thats fine, but just reboot once or twice and make sure it still connects.
Thats were others have had problems.

edit.. You may also have to blacklist some modules to stop desktop freezes etc...

---

