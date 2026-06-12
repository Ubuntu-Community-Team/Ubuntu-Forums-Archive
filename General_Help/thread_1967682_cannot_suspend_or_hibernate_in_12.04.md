---
title: "cannot suspend or hibernate in 12.04"
date: 2012-04-28
forum: General Help
---

### Post by entropy1 on 2012-04-28
I did a fresh install of 12.04 64-bit yesterday, and now I notice that suspend and hibernate do not work.  When I click on suspend or hibernate, everything proceeds normally except that instead of staying suspended or hibernated, the computer immediately wakes up.  Below is the end of /var/log/pm-suspend.log.  Is there other information that would be helpful?

```
Sat Apr 28 10:11:21 CDT 2012: Finished.
Initial commandline parameters: 
Sat Apr 28 10:19:45 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux gubner-tablet 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
pata_pcmcia            17074  1 
tpm_infineon           17536  0 
arc4                   12529  2 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
pcmcia                 49310  1 pata_pcmcia
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlwifi               328352  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
tpm_tis                18804  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506816  1 iwlwifi
wmi                    19256  1 hp_wmi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
cfg80211              205544  2 iwlwifi,mac80211
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
i915                  468651  8 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
drm_kms_helper         46978  1 i915
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  4 i915,drm_kms_helper
intel_ips              18089  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 
             total       used       free     shared    buffers     cached
Mem:       3840728    1906880    1933848          0     290500     982184
-/+ buffers/cache:     634196    3206532
Swap:      4193276          0    4193276

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Apr 28 10:19:45 CDT 2012: performing suspend
Sat Apr 28 10:19:56 CDT 2012: Awake.
Sat Apr 28 10:19:56 CDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Apr 28 10:19:57 CDT 2012: Finished.

```

---

### Post by dino99 on 2012-04-28
check that your /swap partition is at least 4 Gb

---

### Post by entropy1 on 2012-04-28
Thank you, dino99.  But I do have 4 GiB swap, and that wouldn't affect suspend, would it?

---

### Post by tjwilli on 2012-04-28
I just upgraded to 12.04 this morning, and I noticed that hibernate isn't even available anymore when I hit the power button. Suspend is still there, but not hibernate.

---

### Post by MGebhart on 2012-04-28
[http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)

The listing for adding hibernate is at the top of the page.

---

### Post by entropy1 on 2012-04-28
I had already enabled the hibernate option; the problem is that the computer does not stay hibernated.

---

### Post by tjwilli on 2012-04-28
That did it. Thanks. I don't seem to be having the problem that entropy1 is having with not the system not staying suspended or hibernated, but why isn't hibernate enabled in 12.04 by default?

---

### Post by brainwash on 2012-04-28
> **tjwilli said:**
> That did it. Thanks. I don't seem to be having the problem that entropy1 is having with not the system not staying suspended or hibernated, but why isn't hibernate enabled in 12.04 by default?

It's disabled by default to prevent data lose when you except hibernate to work, but unfortunately it is broken in many cases.


**entropy1**, try to remove some of the kernel modules before suspending your system to find the culprit one.

For example, unload the SD card reader:
```
sudo rmmod sdhci_pci
sudo rmmod sdhci
```

---

### Post by entropy1 on 2012-04-28
After more careful reading, I realized that when I said I "had already enabled hibernation," I had followed instructions from another website.  Those instructions were very similar, but put commands in a different file in a different folder.  I removed that file, and followed the instructions suggested by MGebhart.  Now my machine will stay hibernated.  However, it does not stay suspended.  I then followed the suggestions of brainwash, but my machine still does not stay suspended.  To sum up, my hibernation problem is solved, but my suspend problem continues...

---

### Post by entropy1 on 2012-04-29
Bump.

Any suggestions on how to make the computer stay suspended?

---

### Post by entropy1 on 2012-05-01
I solved the suspend problem using the suggestions of posts #7 and #19 in this thread: [http://ubuntuforums.org/showthread.php?t=1444822]("http://ubuntuforums.org/showthread.php?t=1444822")

---

