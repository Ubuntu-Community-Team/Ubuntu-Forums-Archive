---
title: "Can't suspend Asus B43J"
date: 2011-03-15
forum: General Help
---

### Post by Cutler on 2011-03-15
Hello everyone, I have a problem with my new notebook Asus B43J, I can't suspend it under Ubuntu 10.10 32bit. I haven't tried different distributions yet, only LinuxMint and it doesn't work too. When I press suspend, it starts to do something but then it stops on the black screen. I don't know what to do so I include /var/log/pm-suspend. Any help appreciated. Regards.

Initial commandline parameters: 
Tue Mar 15 16:22:26 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux radimj-B43J 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
rfcomm                 33811  8 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   218227  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
radeon                828445  0 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
tpm_infineon            7937  0 
iwlagn                178948  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
i915                  294989  4 
ttm                    56633  1 radeon
iwlcore               127415  1 iwlagn
tpm_tis                 7562  0 
drm_kms_helper         30200  2 radeon,i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
psmouse                59033  0 
tpm                    13741  2 tpm_infineon,tpm_tis
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              11101  0 
asus_laptop            14084  0 
drm                   168092  6 radeon,i915,ttm,drm_kms_helper
tpm_bios                5310  1 tpm
video                  18712  1 i915
btusb                  10969  2 
mac80211              231541  2 iwlagn,iwlcore
output                  1883  1 video
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26694  2 i915
soundcore                880  1 snd
i2c_algo_bit            5168  2 radeon,i915
serio_raw               4022  0 
lp                      7342  0 
sparse_keymap           3145  1 asus_laptop
agpgart                32011  3 ttm,drm,intel_agp
led_class               2633  1 asus_laptop
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
cfg80211              144470  3 iwlagn,iwlcore,mac80211
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19198  2 
libahci                21664  1 ahci
e1000e                132956  0 
             total       used       free     shared    buffers     cached
Mem:       3279164     629960    2649204          0      90216     258672
-/+ buffers/cache:     281072    2998092
Swap:      4095996          0    4095996

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend:

/usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.64 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Mar 15 16:22:28 CET 2011: performing suspend


It says performing suspend but the computer stays on and it's frozen. :-/

---

### Post by Cutler on 2011-03-15
This worked [http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822).

---

