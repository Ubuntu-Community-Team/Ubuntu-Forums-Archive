---
title: "hibernate won't power off"
date: 2011-05-06
forum: General Help
---

### Post by Daniël Slenders on 2011-05-06
Hi

I've got a problem with hibernating my laptop. It manages to copy everything to swap memory, but when it finishes, it won't power off my laptop. I have to manually turn it off (by pressing the power button for a few seconds). If I restart, everything is still there, so the hibernating itself works, but not the powering off part.

My laptop is an Asus notebook K52F with Ubuntu 11.04 and Gnome 3.

thx
Daniël

---

### Post by matt_symes on 2011-05-06
Hi

Could be a whole host of things causing it not to shutdown. To start trouble shooting this have a look at the log file

```
/var/log/pm-suspend.log
```

What does that say ?

Kind regards

---

### Post by Daniël Slenders on 2011-05-13
This is the content of the log file.
What should I be looking for?

```

Initial commandline parameters: 
Sun May  1 18:16:13 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usbhid                 46956  0 
hid                    91020  1 usbhid
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
joydev                 17606  0 
ath9k_hw              323077  2 ath9k,ath9k_common
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    23773  2 ath9k,ath9k_hw
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
cfg80211              178528  3 ath9k,mac80211,ath
i915                  514985  8 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
serio_raw              13166  0 
jmb38x_ms              17596  0 
i2c_algo_bit           13400  1 i915
soundcore              12680  1 snd
lp                     17825  0 
intel_ips              18097  0 
memstick               16520  1 jmb38x_ms
video                  19438  1 i915
parport                46458  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ahci                   25951  3 
libahci                26642  1 ahci
sdhci_pci              13989  0 
jme                    40728  0 
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    3711424     131140          0     960760    1443560
-/+ buffers/cache:    1307104    2535460
Swap:      3998716         68    3998648

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Sun May  1 18:16:16 CEST 2011: performing hibernate
Sun May  1 18:18:38 CEST 2011: Awake.
Sun May  1 18:18:38 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.4 -> dest=:1.257 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sun May  1 18:18:44 CEST 2011: Finished.
Initial commandline parameters: 
Sun May  1 18:23:50 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usbhid                 46956  0 
hid                    91020  1 usbhid
cryptd                 20510  0 
aes_x86_64             17208  2 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
arc4                   12529  2 
snd_hda_intel          33211  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
joydev                 17606  0 
ath9k_hw              323077  2 ath9k,ath9k_common
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    23773  2 ath9k,ath9k_hw
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  10 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
cfg80211              178528  3 ath9k,mac80211,ath
i915                  514985  8 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
serio_raw              13166  0 
jmb38x_ms              17596  0 
i2c_algo_bit           13400  1 i915
soundcore              12680  1 snd
lp                     17825  0 
intel_ips              18097  0 
memstick               16520  1 jmb38x_ms
video                  19438  1 i915
parport                46458  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ahci                   25951  3 
libahci                26642  1 ahci
sdhci_pci              13989  0 
jme                    40728  0 
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    1969068    1873496          0      83484     449716
-/+ buffers/cache:    1435868    2406696
Swap:      3998716     133572    3865144

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Sun May  1 18:23:51 CEST 2011: performing hibernate
Sun May  1 18:25:34 CEST 2011: Awake.
Sun May  1 18:25:35 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sun May  1 18:25:37 CEST 2011: Finished.
Initial commandline parameters: 
Wed May  4 10:42:36 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  514985  8 
uvcvideo               72195  0 
ath9k_common           13851  1 ath9k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              323077  2 ath9k,ath9k_common
videodev               82052  1 uvcvideo
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
v4l2_compat_ioctl32    17078  1 videodev
ath                    23773  2 ath9k,ath9k_hw
jmb38x_ms              17596  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k,mac80211,ath
memstick               16520  1 jmb38x_ms
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
jme                    40728  0 
             total       used       free     shared    buffers     cached
Mem:       3842564     978952    2863612          0      94068     448476
-/+ buffers/cache:     436408    3406156
Swap:      3998716          0    3998716

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed May  4 10:42:38 CEST 2011: performing hibernate
Wed May  4 11:32:16 CEST 2011: Awake.
Wed May  4 11:32:16 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.4 -> dest=:1.74 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed May  4 11:32:17 CEST 2011: Finished.
Initial commandline parameters: 
Wed May  4 11:58:40 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  514985  8 
uvcvideo               72195  0 
ath9k_common           13851  1 ath9k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              323077  2 ath9k,ath9k_common
videodev               82052  1 uvcvideo
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
v4l2_compat_ioctl32    17078  1 videodev
ath                    23773  2 ath9k,ath9k_hw
jmb38x_ms              17596  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k,mac80211,ath
memstick               16520  1 jmb38x_ms
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  5 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
jme                    40728  0 
             total       used       free     shared    buffers     cached
Mem:       3842564    1993792    1848772          0     393412     723688
-/+ buffers/cache:     876692    2965872
Swap:      3998716          8    3998708

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed May  4 11:58:41 CEST 2011: performing hibernate
Wed May  4 12:11:43 CEST 2011: Awake.
Wed May  4 12:11:43 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.4 -> dest=:1.151 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed May  4 12:11:46 CEST 2011: Finished.
Initial commandline parameters: 
Wed May  4 12:44:17 CEST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13851  1 ath9k
i915                  514985  8 
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
uvcvideo               72195  0 
psmouse                73535  0 
soundcore              12680  1 snd
cfg80211              178528  3 ath9k,mac80211,ath
drm_kms_helper         42136  1 i915
videodev               82052  1 uvcvideo
intel_ips              18097  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
jmb38x_ms              17596  0 
memstick               16520  1 jmb38x_ms
v4l2_compat_ioctl32    17078  1 videodev
drm                   227495  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
asus_laptop            24173  0 
video                  19438  1 i915
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
sdhci_pci              13989  0 
ahci                   25951  3 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
jme                    40728  0 
             total       used       free     shared    buffers     cached
Mem:       3842564    1230064    2612500          0     106240     544796
-/+ buffers/cache:     579028    3263536
Swap:      3998716          0    3998716

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed May  4 12:44:20 CEST 2011: performing suspend
Initial commandline parameters: 
Wed May  4 13:22:56 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33211  2 
arc4                   12529  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
mac80211              294370  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
i915                  514985  9 
drm_kms_helper         42136  1 i915
drm                   227495  5 i915,drm_kms_helper
psmouse                73535  0 
jmb38x_ms              17596  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
memstick               16520  1 jmb38x_ms
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
soundcore              12680  1 snd
intel_ips              18097  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              178528  3 ath9k,mac80211,ath
asus_laptop            24173  0 
video                  19438  1 i915
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  4 
jme                    40728  0 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    1658252    2184312          0     103836     794620
-/+ buffers/cache:     759796    3082768
Swap:      3998716          0    3998716

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed May  4 13:22:59 CEST 2011: performing hibernate
Initial commandline parameters: 
Wed May  4 15:46:11 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
ath9k                 118238  0 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              294370  1 ath9k
snd_seq_midi           13324  0 
i915                  514985  8 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
snd_timer              29602  2 snd_pcm,snd_seq
ath                    23773  2 ath9k,ath9k_hw
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
cfg80211              178528  3 ath9k,mac80211,ath
jmb38x_ms              17596  0 
drm_kms_helper         42136  1 i915
memstick               16520  1 jmb38x_ms
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227495  4 i915,drm_kms_helper
psmouse                73535  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
jme                    40728  0 
sdhci_pci              13989  0 
libahci                26642  1 ahci
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    1689624    2152940          0     177516     827740
-/+ buffers/cache:     684368    3158196
Swap:      3998716          0    3998716

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed May  4 15:46:14 CEST 2011: performing hibernate
Thu May  5 18:35:08 CEST 2011: Awake.
Thu May  5 18:35:08 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.314 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Thu May  5 18:35:11 CEST 2011: Finished.
Initial commandline parameters: 
Fri May  6 00:47:45 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  3 bnep
btusb                  18600  2 
bluetooth              72448  8 sco,bnep,l2cap,btusb
usbhid                 46956  0 
hid                    91020  1 usbhid
snd_usb_audio         112426  0 
snd_usbmidi_lib        25139  1 snd_usb_audio
usb_storage            53538  2 
uas                    17996  0 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
ath9k                 118238  0 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96625  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              294370  1 ath9k
snd_seq_midi           13324  0 
i915                  514985  8 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
snd_timer              29602  2 snd_pcm,snd_seq
ath                    23773  2 ath9k,ath9k_hw
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
snd                    67382  19 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
cfg80211              178528  3 ath9k,mac80211,ath
jmb38x_ms              17596  0 
drm_kms_helper         42136  1 i915
memstick               16520  1 jmb38x_ms
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227495  4 i915,drm_kms_helper
psmouse                73535  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
jme                    40728  0 
sdhci_pci              13989  0 
libahci                26642  1 ahci
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    3462320     380244          0     656824    1503028
-/+ buffers/cache:    1302468    2540096
Swap:      3998716        112    3998604

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Fri May  6 00:47:47 CEST 2011: performing hibernate
Initial commandline parameters: 
Fri May  6 21:37:07 CEST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Daniel-LAPTOP 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
arc4                   12529  2 
snd_hda_intel          33211  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 118238  0 
i915                  514985  9 
snd_seq_midi           13324  0 
mac80211              294370  1 ath9k
snd_rawmidi            30486  1 snd_seq_midi
uvcvideo               72195  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
psmouse                73535  0 
ath9k_common           13851  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
ath9k_hw              323077  2 ath9k,ath9k_common
videodev               82052  1 uvcvideo
ath                    23773  2 ath9k,ath9k_hw
jmb38x_ms              17596  0 
drm_kms_helper         42136  1 i915
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k,mac80211,ath
memstick               16520  1 jmb38x_ms
intel_ips              18097  0 
drm                   227495  5 i915,drm_kms_helper
snd                    67382  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
jme                    40728  0 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       3842564    3810608      31956          0    1080996    1152344
-/+ buffers/cache:    1577268    2265296
Swap:      3998716         12    3998704

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Fri May  6 21:37:11 CEST 2011: performing hibernate
Sat May 14 01:33:48 CEST 2011: Awake.
Sat May 14 01:33:49 CEST 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.116 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sat May 14 01:34:05 CEST 2011: Finished.
```

---

### Post by matt_symes on 2011-05-13
Hi

The only issue i can see in that file is
[FONT=monospace]
[/FONT]> 
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: Having NetworkManager put all interaces to sleep...Failed. 
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success. 
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: 
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directoryAre you using wicd (or something else) and not network manager ?

Kind regards

---

### Post by Daniël Slenders on 2011-05-14
No, I'm using NetworkManager (the one which comes with Ubuntu).

Daniël

PS
thx for quick reply

---

### Post by matt_symes on 2011-05-14
Hi

I currently have a problem with hibernation on my laptop so i am really looking into the whole process.

Lets start with the basics. You have to have enough free swap to hibernate. Looking at your pm-suspend log it seems you have.

Let's immediately eliminate something. Open a terminal and type

```
sudo service network-manager stop
```

Enter your password. It will not be echoed to the screen. Then type

```
sudo pm-hibernate
```

What is the outcome of hibernating that way ?

Kind regards

---

### Post by Daniël Slenders on 2011-05-14
It has the same result as before.

What appears on the screen when hibernating is:
```
Looking for splash system... none
s2disk: Snapshotting system
s2disk: System snapshot ready. Preparing to write
s2disk: Image size: 1772216 kilobytes
s2disk: Free swap: 3683100 kilobytes
s2disk: Saving 443053 image data pages(press backspace to abort)... 100% done (443053 pages)
SI

```

Daniël

---

### Post by matt_symes on 2011-05-14
Hi

Alright lets move down to the kernel level directly.

Try this. Enter these two commands into a terminal, one after another.

```
sudo bash -c "echo platform > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"
```

That will attempt to hibernate your pc without calling any of the hibernate hooks. It will create the disk image for you and then attempt to use the ACPI framework to hibernate.

If that does not work try

```
sudo bash -c "echo shutdown > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"
```

The second set of commands will try to hibernate without calling some of the ACPI framework.

Tell me how that goes.

Kind regards

---

### Post by Daniël Slenders on 2011-05-14
```
sudo bash -c "echo platform > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"
```
This one did the same as before: hibernating without powering off. One difference: it didn't show anything on the screen. While making the snapshot, there was a blinking hyphen; when that finished, the screen was just blank (but still on).

```
sudo bash -c "echo shutdown > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"
```
This one worked great! It did everything as it should, but when coming out of hibernation, there was an error. I didn't have time to read it, because it disappaered very quickly. Anyway, it resumed correctly.


How can I put that set of commands in the hibernate script?


Thanks for your help,
Daniël

---

### Post by Daniël Slenders on 2011-05-14
The error was:
```

[24000.053522] rndis_host 2_1.2:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47

```

---

### Post by matt_symes on 2011-05-14
Hi

> **Daniël Slenders said:**
> The error was:
```

[24000.053522] rndis_host 2_1.2:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47

```

It would seem you have a problem with ACPI and shutting down. I need to research that error message before i offer any solutions though.

The solution could be as simple as a kernel boot line argument.

I will get back to you.

Kind regards

---

### Post by matt_symes on 2011-05-14
Hi

Can you post the output of these two command (copy and paste then into the terminal)

```
lsusb
```

and

```
sudo lshw -C network
```

Kind regards

---

### Post by Daniël Slenders on 2011-05-14
```


daniel@Daniel-LAPTOP:~$ lsusb
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```

daniel@Daniel-LAPTOP:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:a6:8a:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.124 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2c00000-d2c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: 48:5b:39:25:84:76
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)

```

---

### Post by matt_symes on 2011-05-15
Hi

There are a couple of options that i know of at the moment. One of the options is to disable acpi from the kernel command line. This may enable you to hibernate properly. However it may or may not also have other effects on your system. It would be a case of trying it and seeing what happens. It is reversible.

Another option is to try to identify exactly what is causing ACPI to fail. This may be one piece of the hardware on your system. We may be able to get around that by unloading the driver for it before hibernating as it may contain buggy code.

We can try to see if it's a statically linked driver in the kernel by booting into a minimal shell /bin/bash and trying to hibernate using platform mode. That should narrow down hardware drivers from those statically compiled into the kernel and those that are dynamically loaded kernel modules.

It depends how you feel about tracking down the issue. I can throw things at you to try but it may get rather technical. Even then i can't guarantee i can help you fix it. We can try though. 

What do you think ?

Kind regards

---

### Post by Daniël Slenders on 2011-05-16
> **matt_symes said:**
> Hi

There are a couple of options that i know of at the moment. One of the options is to disable acpi from the kernel command line. This may enable you to hibernate properly. However it may or may not also have other effects on your system. It would be a case of trying it and seeing what happens. It is reversible.

Does acpi do anything else that's not related to power management?

> **matt_symes said:**
> 
Another option is to try to identify exactly what is causing ACPI to fail. This may be one piece of the hardware on your system. We may be able to get around that by unloading the driver for it before hibernating as it may contain buggy code.

We can try to see if it's a statically linked driver in the kernel by booting into a minimal shell /bin/bash and trying to hibernate using platform mode. That should narrow down hardware drivers from those statically compiled into the kernel and those that are dynamically loaded kernel modules.

I did have the same problem on Ubuntu 10.10 and 10.04, but I don't know if they updated the drivers since. At the moment, I have the latest drivers availlable (as far as i know).

> **matt_symes said:**
> 
It depends how you feel about tracking down the issue. I can throw things at you to try but it may get rather technical. Even then i can't guarantee i can help you fix it. We can try though. 

What do you think ?

Kind regards
I'm willing to try anything...

---

### Post by matt_symes on 2011-05-16
Hi

> **Daniël Slenders said:**
> Does acpi do anything else that's not related to power management?

I believe it also can handle things like irq routing and hyper threading.

> 
I did have the same problem on Ubuntu 10.10 and 10.04, but I don't know if they updated the drivers since. At the moment, I have the latest drivers availlable (as far as i know).

I'm willing to try anything...Let's try the sledge hammer approach to start with and disable acpi completely. You will need to edit your /etc/default/grub file.

Open a terminal and type

```
sudo nano /etc/default/grub
```Look for the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

```Ctrl + o to save the file, then ctrl + x to exit. Then you need to rebuild grub.

```
sudo update-grub
```Reboot your PC and from the command line check the new kernel option is there by typing

```
cat /proc/cmdline
```Then try to hibernate. What happens ?

Kind regards

---

### Post by outleradam on 2011-05-29
> **matt_symes said:**
> Hi



I believe it also can handle things like irq routing and hyper threading.

Let's try the sledge hammer approach to start with and disable acpi completely. You will need to edit your /etc/default/grub file.

Open a terminal and type

```
sudo nano /etc/default/grub
```Look for the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

```Ctrl + o to save the file, then ctrl + x to exit. Then you need to rebuild grub.

```
sudo update-grub
```Reboot your PC and from the command line check the new kernel option is there by typing

```
cat /proc/cmdline
```Then try to hibernate. What happens ?

Kind regards
just tried that on my computer which is having the same issue.  It's an Asus A72F. The mouse stopped working.   The power button functioned as an old skool on-off button.  



Any other suggestions?

---

### Post by Daniël Slenders on 2011-05-30
Same problems with me, although it's only touchpad that's not working. An external mouse still works.


grtz
Daniël

PS
sorry for late reply, but I didn't have access to my laptop lately.

---

