---
title: "maverick problem: suspend to ram"
date: 2010-11-09
forum: General Help
---

### Post by james1415 on 2010-11-09
A few days ago I did  a clean install of maverick meercat (kubuntu version) on my Dell XPS M1530. I have just 2 problems (which I'll post separately):

I have set the system to suspend to RAM when  closing the lid. However this isn't working properly:

- either nothing happens when the lid is closed, even the screen stays on, 
or, more commonly,
- the laptop won't wake up when the lid is opened.  The disk spins and the lights work (eg wireless), but the screen remains blank and I can't get anything to work.

Any suggestions?

Thanks - James

---

### Post by 0N3 on 2010-11-09
Have you created a swap partition during the install?

---

### Post by james1415 on 2010-11-10
Yes - 9.3 Gb of swap (and 4Gb ram).

James


ps Save to disk works ok - it's just save to ram
pps But not always!  I just had the same problem but with the save to disk setting.

---

### Post by ULtimeeTje on 2010-11-29
I have the same problem on my Dell Latitude E6500.
However I didn't do the clean install, I performed a dist-upgrade from 10.04.

---

### Post by matt_symes on 2010-11-29
Hi

Are there any clues in you log file? It's located in

/var/log/pm-suspend.log

Kind regards

---

### Post by ULtimeeTje on 2010-11-29
this is the output from my last try...
I don't see any immediate errors.


> Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Mon Nov 29 13:05:54 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ca60c464 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
hidp                   15019  0 
rfcomm                 40755  6 
binfmt_misc             7984  1 
sco                     9954  2 
bnep                   11985  2 
l2cap                  42304  17 hidp,rfcomm,bnep
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792824  2 vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_idt      64667  1 
btusb                  12929  2 
bluetooth              59213  10 hidp,rfcomm,sco,bnep,l2cap,btusb
joydev                 11363  0 
arc4                    1497  2 
snd_hda_intel          26019  4 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
i915                  330249  3 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
drm_kms_helper         32836  1 i915
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlagn                202721  0 
pcmcia                 40944  0 
drm                   206161  4 i915,drm_kms_helper
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               146875  1 iwlagn
snd                    64117  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62379  0 
mac80211              266657  2 iwlagn,iwlcore
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
dell_wmi                3372  0 
v4l2_compat_ioctl32    12486  1 videodev
yenta_socket           24279  0 
pcmcia_rsrc            10357  1 yenta_socket
dell_laptop             6722  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
dcdbas                  6910  1 dell_laptop
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                62080  0 
tpm_tis                 9894  0 
serio_raw               4910  0 
cfg80211              170293  3 iwlagn,iwlcore,mac80211
intel_agp              32080  2 i915
i2c_algo_bit            6208  1 i915
tpm                    16013  1 tpm_tis
tpm_bios                6426  1 tpm
video                  22176  1 i915
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  2 hidp,usbhid
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
ahci                   21857  0 
libahci                26167  4 ahci
e1000e                151787  0 
             total       used       free     shared    buffers     cached
Mem:       3943204    2008200    1935004          0     200116     796996
-/+ buffers/cache:    1011088    2932116
Swap:      8000364          0    8000364

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
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.70 reply_serial=2
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
Running hook /usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:

/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Mon Nov 29 13:05:56 CET 2010: performing suspend

---

### Post by ULtimeeTje on 2010-11-30
I have the same issue as [this thread]("http://ubuntuforums.org/showpost.php?p=10137227&postcount=17")

When I change the permissions of those files everything works but when I reboot the changes are gone... Is there any way to configure the permissions?

---

### Post by ULtimeeTje on 2010-12-01
the latest kernel update (2.6.35-23-generic) seems to fix the problem...

---

### Post by james1415 on 2010-12-01
Yup -seems to work now. 
Thank-you kernel updaters!
James

---

### Post by Byb on 2010-12-20
Is the bug come back ?
My fresh install can't wake up from ram also. To have the visual effects working, I have only forced and locked xserver-xorg-video-intel to 2:2.12.0-1ubuntu5.1 and added this /etc/X11/xorg.conf as advised elsewhere:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```Is there a relation please?
Also my own home folder is encrypted with ecrypt-migrate-home -u ... and swap with ecrypt-setup-swap as recommanded. (I abandonned the suspend-to-disk feature as stated by the command - although, the hibernate item is sometimes displayed in the gnome logoff menu). This is said to prevent suspend-to-disk, not suspend-to-ram.
Here is the pm-suspend.log (don't know what to search)
```
Initial commandline parameters: 
Mon Dec 20 15:55:59 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 **2.6.37-997-generic** #201012190905 SMP Sun Dec 19 10:23:39 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
lib80211_crypt_ccmp     4573  2 
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  188 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
joydev                  9423  0 
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
ipw2200               140899  0 
pcmcia                 37586  0 
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 40474  1 ipw2200
yenta_socket           20749  0 
cfg80211              144857  2 ipw2200,libipw
pcmcia_rsrc            10372  1 yenta_socket
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore                880  1 snd
psmouse                58014  0 
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lp                      7400  0 
serio_raw               4062  0 
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 501909  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  513670  3 
drm_kms_helper         32088  1 i915
drm                   182490  4 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25335  0 
i2c_algo_bit            4910  1 i915
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009088     432620     576468          0      41244     227588
-/+ buffers/cache:     163788     845300
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.1 -> dest=:1.54 reply_serial=2
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
Mon Dec 20 15:56:02 CET 2010: performing suspend

```Thanks in advance for your help

---

### Post by ULtimeeTje on 2010-12-20
I haven't had any problems since I upgraded my kernel to 2.6.36...

---

### Post by Byb on 2010-12-20
I was advised to update to workaround the visual effects issue :sad:

---

### Post by lazyfirecloud on 2011-01-05
I have Ubuntu Maverick (Not Kubuntu) with kernel 2.6.35-24 (latest from repository) and I am still seeing the same issue (lights turns on, no monitor). Does anyone have any idea?
I didn't have an issue until I upgraded to Maverick.

---

### Post by Byb on 2011-01-05
I'm with gnome (too?) and I tried all the rc up to the latest 2.6.37-rc8-natty stll same issue.
I will try the current natty 20110105 now.
Do you know the use of the 000x.aaaaa-bbbbbb.patch files?
thanks and happy new year

---

### Post by lazyfirecloud on 2011-01-05
No, I've never patched the kernel. That's a bummer to hear it still doesn't work upstream. I keep hoping it will be fixed every time I do a kernel upgrade. It works 75% of the time and won't wake the last 25%. I can't figure out what triggers it not to wake up and there are no errors that I can see in the /var/log/pm-suspend.log . I guess I'll just keep looking for an answer, or be very careful to save my work =)

Not sure if that's useful, but I did find some failure to resume in /var/log/dmesg.

```

[    1.930180] ACPI Error (psargs-0359): [NPSS] Namespace lookup failure, AE_NOT_FOUND
[    1.930191] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff8801534e1c00), AE_NOT_FOUND
[    1.930335] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff8801534e1b20), AE_NOT_FOUND
[    1.932272] ACPI Error (psargs-0359): [NPSS] Namespace lookup failure, AE_NOT_FOUND
[    1.932277] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff8801534e1c00), AE_NOT_FOUND
[    1.932361] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff8801534e1b20), AE_NOT_FOUND
[    1.932426] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PPC] (Node ffff8801534e1be0), AE_NOT_FOUND
[    1.933483] ACPI Error (psargs-0359): [NPSS] Namespace lookup failure, AE_NOT_FOUND
[    1.933493] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff8801534e1c00), AE_NOT_FOUND
[    1.933601] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff8801534e1b20), AE_NOT_FOUND
[    1.933650] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PPC] (Node ffff8801534e1dc0), AE_NOT_FOUND
[    1.935318] ACPI Error (psargs-0359): [NPSS] Namespace lookup failure, AE_NOT_FOUND
[    1.935322] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0.PPC_] (Node ffff8801534e1c00), AE_NOT_FOUND
[    1.935391] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PPC] (Node ffff8801534e1b20), AE_NOT_FOUND
[    1.935440] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU3._PPC] (Node ffff8801534e1d40), AE_NOT_FOUND
[    1.935681] ACPI: Battery Slot [BAT0] (battery present)
[    1.935776] PM: Resume from disk failed.

```

---

### Post by Byb on 2011-01-06
It seems we poor noobs are assigned the same beta tester status that one blame M$ to do with zin users.

---

### Post by lazyfirecloud on 2011-01-06
Well there seems to be a related bug already filed and confirmed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091)
so maybe it will be fixed eventually =)

---

### Post by Byb on 2011-01-07
Here is a thread with maybe-perhaps-who-knows magic incantations that could make ubuntu working ... eventually. After reading it and got a headache, I posted my own malediction. God will possibly reply.

[http://ubuntuforums.org/showthread.php?t=1596545](http://ubuntuforums.org/showthread.php?t=1596545)

---

### Post by lazyfirecloud on 2011-01-07
Thanks for the link =) I've change the /etc/default/acpi-support and been disabling my wireless before suspend. Since I only get the problem 20% of the time, I'll have to wait to see if it helps.

---

