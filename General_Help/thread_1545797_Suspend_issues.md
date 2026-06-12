---
title: "Suspend issues"
date: 2010-08-04
forum: General Help
---

### Post by gabrielcik on 2010-08-04
Hello,

My netbook take ages to Suspend.

Everything starts in good way, i press suspend and all light turn off in few seconds but then before the power light became red and the screen swich off completely pass about 1 minute.

When I resume, it is very fast just few seconds.

I use Ubuntu Lucid on a Sony Vaio W with 2 GB RAM and a OCZ SSD 30 GB.

I don't have any swap partition due to the 30 GB and the SSD.

Hope for a reply:)

---

### Post by sydbat on 2010-08-04
> **gabrielcik said:**
> Hello,

My netbook take ages to Suspend.

Everything starts in good way, i press suspend and all light turn off in few seconds but then before the power light became red and the screen swich off completely pass about 1 minute.

When I resume, it is very fast just few seconds.

I use Ubuntu Lucid on a Sony Vaio W with 2 GB RAM and a OCZ SSD 30 GB.

I don't have any swap partition due to the 30 GB and the SSD.

Hope for a reply:)Well, no swap is likely your problem. If you want to use the suspend features, you need a swap partition that is *at least* as large as your RAM (twice as large would be better).

---

### Post by Mi11z on 2010-08-04
> **gabrielcik said:**
> Hello,

My netbook take ages to Suspend.

Everything starts in good way, i press suspend and all light turn off in few seconds but then before the power light became red and the screen swich off completely pass about 1 minute.

When I resume, it is very fast just few seconds.

I use Ubuntu Lucid on a Sony Vaio W with 2 GB RAM and a OCZ SSD 30 GB.

I don't have any swap partition due to the 30 GB and the SSD.

Hope for a reply:)

All i can really say is that has always been issues with ubuntu suspension and especially hibernation, so all i can suggest is do some google hunting or just wait for someone more experienced to reply. :)

---

### Post by gabrielcik on 2010-08-04
Thank you for the replies.

I didn't know i had to use a swap partition for to Suspend. I thought it is required only for to hibernate.

Anyway i will try to create it and give a try even if i would prefer to stay without since im afraid to spoil my SSD.

I have also another strange issue. When i resume the first thing i get is a black screen. Only if i move again the mouse or press a button i finally get the desktop.

---

### Post by sydbat on 2010-08-04
> **gabrielcik said:**
> Thank you for the replies.

I didn't know i had to use a swap partition for to Suspend. I thought it is required only for to hibernate.

Anyway i will try to create it and give a try even if i would prefer to stay without since im afraid to spoil my SSD.

I have also another strange issue. When i resume the first thing i get is a black screen. Only if i move again the mouse or press a button i finally get the desktop.Well, if they are only minor annoyances, then do not worry about them. Leave things as they are and you won't have to stress about 'breaking' anything.

---

### Post by gabrielcik on 2010-08-04
I tried creating a swap file but nothing has changed. It still take a lot of time.

With different netbook i didn't have the same issue.

---

### Post by gabrielcik on 2010-08-04
Hello,

I tried to run this command: pmi action suspend, and happened the same...

All light swich off (wifi, hd, etc...) but the display stay on and everything freeze for more than 30 secs.

Where can i find the reason of this freezing?

---

### Post by gabrielcik on 2010-08-04
how can i see the output of the suspend command?
(i would like to see what happen when i press such button and so why it freeze)

---

### Post by gabrielcik on 2010-08-05
Hello,

I post my suspend long, hoping somebody can help me to solve my problem.

> 
Initial commandline parameters: 
Thu Aug  5 15:54:07 CEST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux  gabrielcik-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14  UTC 2010 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
rfcomm                 33421  0 
sco                     7885  0 
bridge                 45582  0 
stp                     1655  1 bridge
ppdev                   5259  0 
bnep                    9436  0 
l2cap                  30624  4 rfcomm,bnep
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  72 
snd_seq_oss            26726  0 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
joydev                  8708  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq
i915                  285076  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 306010  0 
drm_kms_helper         29297  1 i915
mac80211              205146  1 ath9k
ath                     7611  1 ath9k
snd                    54148  16  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
uvcvideo               56990  0 
sdhci_pci               5470  0 
cfg80211              126517  3 ath9k,mac80211,ath
intel_agp              24119  2 i915
soundcore               6620  1 snd
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sony_laptop            28248  0 
psmouse                63245  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 ath9k,sdhci
video                  17375  1 i915
serio_raw               3978  0 
atl1c                  28083  0 
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
btusb                  10925  0 
bluetooth              49892  7 rfcomm,sco,bnep,l2cap,btusb
             total       used       free     shared    buffers     cached
Mem:       2052400     701176    1351224          0      47512     402680
-/+ buffers/cache:     250984    1801416
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Aug  5 15:54:08 CEST 2010: performing suspend
Thu Aug  5 15:54:55 CEST 2010: Awake.
Thu Aug  5 15:54:55 CEST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Aug  5 15:54:56 CEST 2010: Finished.


If i try to run the command sleep.sh in /etc/acpi i get this error:

> cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory


I can suspend from terminal running pm-suspend (but still it freeze for long before suspend).

Where can i change the setting for the suspend command?

---

### Post by efflandt on 2010-08-05
You do NOT need swap for suspend, only for hibernate.

It does not appear to take a long time from pm-suspend.log:
Thu Aug  5 15:54:07 CEST 2010: Running hooks for suspend.
...
Thu Aug  5 15:54:08 CEST 2010: performing suspend

Although, maybe something is slow after that.  Suspend issues are often related to video.  What video chip do you have and are you running non-default (proprietary) driver for it?

One old PC of mine would not go into suspend (video blanked but did not turn off) until I used **nomodeset** kernel boot parameter (apparently did not like new kms video drivers which also slowed down video).

Another had 2 suspend/hibernate issues, kept trying to poll a non-existing floppy (hot swap drive bay), so I had to blacklist floppy.  And I also had to blacklist intel_agp and use NvAGP for nvidia(96) driver [don't have to do that with newer GT220 with nvidia(195) driver].

---

### Post by gabrielcik on 2010-08-05
My netbook is a Vaio VPCW12J1E with 2 GB of ram.

The video card is:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

I believe it is not using a proprietary driver (under Hardware drivers there is not such).

Thank you!

---

### Post by gabrielcik on 2010-08-06
I have tried to switch the intel device to vesa in xorg.conf, but the result was still the same. It still freeze before to suspend.

any idea about what can be the problem?

---

### Post by gabrielcik on 2010-08-07
I noticed this in the sys log:

Aug  7 15:21:41 gabrielcik-laptop wpa_supplicant[681]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  7 15:22:29 gabrielcik-laptop kernel: [11455.481501] PM: Syncing filesystems ... done.
Aug  7 15:22:29 gabrielcik-laptop kernel: [11455.513181] PM: Preparing system for mem sleep

So it seems the "freeze" is due to the Syncing filesystems, is there a way to make it goes faster?

I don't know if it matters, but im using only 1 partition with ext4 journalled and without swap on a OCZ SSD 30GB.

Hoping for a reply:)

---

