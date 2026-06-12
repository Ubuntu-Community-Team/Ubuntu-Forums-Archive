---
title: "Won't properly suspend"
date: 2010-05-25
forum: General Help
---

### Post by whalogreg on 2010-05-25
Using Ubuntu 10.04 64bit on a Gateway MD7818u. When trying to suspend, the laptop shows a black screen and locks, but the screen remains on, and that is all that appears to happen. The fan, hard drive, wifi, everything remains on. The hard drive doesn't spin down, the screen doesn't shut off, the computer remains completely on, only a black lit-up screen that locks. What can I do to try to troubleshoot this problem?

---

### Post by whalogreg on 2010-05-26
bump

---

### Post by whalogreg on 2010-05-28
Anyone? I've been reading up on suspend problems and most I've found revolve around problems returning from suspend/hibernate. I've had no problems with hibernate...

---

### Post by keypox on 2010-05-28
Im going back to 9.10.  Hopefully it fixes it for me.  Crazy part for me is that it was working then just stopped suddenly  reinstalls havnet fixed it.  

Windows still works.

---

### Post by whalogreg on 2010-05-29
Well, I don't find the issue bad enough to revert to 9.10, but it is annoying. I've had a few problems with 10.04 but about half of them have worked out with some system updates. I wonder if this will as well, or maybe it's a compatibility problem with my hardware..

---

### Post by keypox on 2010-05-29
I think mine might be a hardware issue. Maybe Nvidia drivers... i dunno but there are many threads on it.  Seems like something is up. 

9.10 didnt work for me any how. Either did fedora 13...

---

### Post by keypox on 2010-05-29
Here is where the suspend log is.  Though mine says all success but it is not.

run in terminal
      gedit /var/log/pm-suspend.log

Found from here [http://forums.linuxmint.com/viewtopic.php?f=49&t=48402](http://forums.linuxmint.com/viewtopic.php?f=49&t=48402)

I wish I could find out what is causing suspend to fail!!!  Then I could fix the fffff problem.

---

### Post by whalogreg on 2010-05-30
Well, this is what i've found in my suspend log..

```

Initial commandline parameters: 
Sun May  2 11:52:30 EDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux greg-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768247  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_conexant    28745  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
softcursor              1565  1 bitblit
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
arc4                    1473  2 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
i915                  317872  3 
uvcvideo               62403  0 
iwlagn                121577  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         30742  1 i915
iwlcore               124955  1 iwlagn
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
mac80211              238128  2 iwlagn,iwlcore
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               6700  0 
videodev               40486  1 uvcvideo
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
psmouse                64608  0 
v4l1_compat            15495  2 uvcvideo,videodev
sdhci                  17928  1 sdhci_pci
v4l2_compat_ioctl32    12020  1 videodev
joydev                 11072  0 
cfg80211              148386  3 iwlagn,iwlcore,mac80211
serio_raw               4918  0 
led_class               3732  2 iwlcore,sdhci
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  20623  1 i915
soundcore               8052  1 snd
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ahci                   37646  2 
sky2                   48803  0 
             total       used       free     shared    buffers     cached
Mem:       3922604    1142292    2780312          0      85340     491016
-/+ buffers/cache:     565936    3356668
Swap:     10490404          0   10490404
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_sound-after-resume suspend suspend:lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
Terminating processes: 1371lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2774lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2791lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2808lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2825lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2843(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2843(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Returned exit code 1.

Sun May  2 11:52:38 EDT 2010: Inhibit found, will not perform suspend

Sun May  2 11:52:38 EDT 2010: Running hooks for resume
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Initial commandline parameters: 
Sun May  2 23:06:50 EDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux greg-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768247  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_conexant    28745  1 
snd_hda_intel          25645  2 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
softcursor              1565  1 bitblit
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
vga16fb                12757  0 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                9857  1 vga16fb
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
arc4                    1473  2 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
i915                  317872  3 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30742  1 i915
snd_timer              23553  2 snd_pcm,snd_seq
uvcvideo               62403  0 
drm                   198770  4 i915,drm_kms_helper
videodev               40486  1 uvcvideo
iwlagn                121577  0 
i2c_algo_bit            6024  1 i915
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               124955  1 iwlagn
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64608  0 
video                  20623  1 i915
v4l1_compat            15495  2 uvcvideo,videodev
soundcore               8052  1 snd
mac80211              238128  2 iwlagn,iwlcore
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  2 iwlcore,sdhci
output                  2503  1 video
v4l2_compat_ioctl32    12020  1 videodev
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  2 i915
joydev                 11072  0 
cfg80211              148386  3 iwlagn,iwlcore,mac80211
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
sky2                   48803  0 
ahci                   37646  2 
             total       used       free     shared    buffers     cached
Mem:       3922604    1763432    2159172          0      97588     712344
-/+ buffers/cache:     953500    2969104
Swap:     10490404      25256   10465148
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_sound-after-resume suspend suspend:lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
Terminating processes: 1601lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 10383lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 10412lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 10428lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 10446lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 10463(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 10463(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Returned exit code 1.

```

Can anyone help with this info?

---

### Post by bertmanphx on 2010-05-30
Hello,
Try adding "noapic" to the grub boot loader.   If your new to this, boot, then follow the prompts at the bottom of the Grub bootloader to add the line.

bertmanphx

---

### Post by whalogreg on 2010-05-30
I tried the noapic line and it didn't seem to have any noticeable effects.. here's the suspend log after adding the noapic line..

```

Initial commandline parameters: 
Sun May  2 11:52:30 EDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux greg-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768247  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_conexant    28745  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
softcursor              1565  1 bitblit
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
arc4                    1473  2 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
i915                  317872  3 
uvcvideo               62403  0 
iwlagn                121577  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         30742  1 i915
iwlcore               124955  1 iwlagn
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
mac80211              238128  2 iwlagn,iwlcore
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               6700  0 
videodev               40486  1 uvcvideo
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
psmouse                64608  0 
v4l1_compat            15495  2 uvcvideo,videodev
sdhci                  17928  1 sdhci_pci
v4l2_compat_ioctl32    12020  1 videodev
joydev                 11072  0 
cfg80211              148386  3 iwlagn,iwlcore,mac80211
serio_raw               4918  0 
led_class               3732  2 iwlcore,sdhci
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  20623  1 i915
soundcore               8052  1 snd
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ahci                   37646  2 
sky2                   48803  0 
             total       used       free     shared    buffers     cached
Mem:       3922604    1142292    2780312          0      85340     491016
-/+ buffers/cache:     565936    3356668
Swap:     10490404          0   10490404
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_sound-after-resume suspend suspend:lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
Terminating processes: 1371lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2774lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2791lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 2808lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2825lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2843(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/greg/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2843(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-intelhdmi snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Returned exit code 1.

```

---

### Post by whalogreg on 2010-05-30
Well, I seem to have solved this problem, but re-opened an old one.. Before upgrading to 10.04, I had a problem with no sound after returning from suspend/hibernate. I found a script that resolved this problem, but I guess after upgrading from 9.10 the script no longer played nice with Ubuntu. With this script removed, suspend/hibernate all work properly, but I have no sound after resuming... Time to find another work around...

---

