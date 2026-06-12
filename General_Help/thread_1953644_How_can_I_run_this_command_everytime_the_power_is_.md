---
title: "How can I run this command everytime the power is unplugged?"
date: 2012-04-06
forum: General Help
---

### Post by jonnyboysmithy on 2012-04-06
Hi! I want to run this command everytime my power is plugged in or unplugged.
```
sudo hdparm -B 255 /dev/sda
```It is to stop my disk from turning off every 8seconds when I unplug the power. 
At the moment I have a script that runs at boot, but it goes back to powersave mode when I unplug it and it cycles a lot (its got 79873 load unload cycles :shock:I don't think its a good idea to make it do more!:smile:)

How can I do this?

---

### Post by jonnyboysmithy on 2012-04-06
bump

---

### Post by Toz on 2012-04-06
Create an executable file in the directory /etc/pm/power.d. The file will be executed every time the power status changes. The file will be run with root privileges, so sudo won't be required. Something like this:
```
#!/bin/bash
hdparm -B 255 /dev/sda
```

---

### Post by jonnyboysmithy on 2012-04-06
> **Toz said:**
> Create an executable file in the directory /etc/pm/power.d. The file will be executed every time the power status changes. The file will be run with root privileges, so sudo won't be required. Something like this:
```
#!/bin/bash
hdparm -B 255 /dev/sda
```
Thanks for that. Thats exactly what I needed to know.
Edit: I had to restart for it to take effect. Works nicely now.
Edit2: thought it was working, but isn't. disk still powers off when I unplug the laptop.

---

### Post by jonnyboysmithy on 2012-05-05
Bump, I also need it to run the command whenever it wakes up from suspend. How do I do this?

---

### Post by Toz on 2012-05-05
Place the file in /etc/pm/sleep.d so it looks like this:
```
#!/bin/bash

case "${1}" in
    hibernate|suspend)
       # do nothing
       ;;
    resume|thaw)
       /sbin/hdparm -B 255 /dev/sda
       ;;
esac

```

---

### Post by jonnyboysmithy on 2012-05-05
> **Toz said:**
> Place the file in /etc/pm/sleep.d so it looks like this:
```
#!/bin/bash

case "${1}" in
    hibernate|suspend)
       # do nothing
       ;;
    resume|thaw)
       /sbin/hdparm -B 255 /dev/sda
       ;;
esac

```
Thanks!! :popcorn:
Edit: tested, and stops the disk from powering off when idling after waking up from suspend.

---

### Post by jonnyboysmithy on 2012-05-05
Could you help me? Earlier In post #4 I posted that the problem was fixed. Apparently it isn't. When I unplug the laptop the disk will still power off after idling for a few seconds.
I have a script in /etc/pm/power.d/ the name of the file is hdparm-stop-disk-idling Thats an ok name right?
The script is marked as executable and the code is as follows:
```
#!/bin/bash
hdparm -B 255 /dev/sda
```

Ideas?

---

### Post by Toz on 2012-05-05
Try renaming the file to 99-hdparm-stop-disk-idling so that it is the last file being run (in case another file is changing the value back). I think that file might be /usr/lib/pm-utils/power.d/95hdparm-apm.

If the hard drive parking is driving you crazy, I believe you can turn it off totally by adding **nohdparm** to your kernel command line. I did this back in 11.04 with my previous laptop and it worked. If you look at the file **/usr/lib/pm-utils/power.d/95hdparm-apm**, you'll notice the following code:
```
if grep -wq "nohdparm" /proc/cmdline ; then
    exit 0
fi
```

Basically, if nohdparm exists in the kernel command line, it exits this script. This script is the script that enables hard drive parking as a power-saving feature.

---

### Post by jonnyboysmithy on 2012-05-05
How do I go about adding nohdparm to the cmdline?
I edited, but it keeps changing back to what it was.
I renamed it to 99-hdparm-stop-disk-idling didn't seem to make a difference.

---

### Post by Toz on 2012-05-05
> **jonnyboysmithy said:**
> How do I go about adding nohdparm to the cmdline?


As root, edit the **/etc/default/grub** file:
```

gksudo gedit /etc/default/grub
```
...and to the line starting GRUB_CMDLINE_LINUX_DEFAULT, add nohdparm as an option. Example:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohdparm"
```
***NOTE: your line may be different. Don't just use my line, but add nohdparm to your line ensuring that it is within the quotes.

Then run:
```
sudo update-grub
```
...to make it permanent.

---

### Post by jonnyboysmithy on 2012-05-05
So now I can remove the other scripts I made because hdparm is now disabled system wide. Correct?

---

### Post by Toz on 2012-05-06
Yes, they shouldn't be needed anymore. Does the nohdparm parameter work for you?

---

### Post by jonnyboysmithy on 2012-05-06
> **Toz said:**
> Yes, they shouldn't be needed anymore. Does the nohdparm parameter work for you?
Nope, I don't know why. Maybe I should just reflash the drive's firmware with the software provided by the manufacturer. The 16bit software is a pain to run from msdos enviroment. And even if I did that hdparm would override the firmware settings right? So I would be better to get hdparm working?

---

### Post by Bandit on 2012-05-06
Some BIOS's can have built in power management over the drives, video, network and USB. Check there incase they are overiding the OS.

---

### Post by jonnyboysmithy on 2012-05-06
> **Bandit said:**
> Some BIOS's can have built in power management over the drives, video, network and USB. Check there incase they are overiding the OS.
Checked. Nothing about power management or harddrive in the bios.

---

### Post by Toz on 2012-05-06
After booting with the nohdparm kernel parameter, can you post back the results of:
```
cat /proc/cmdline
```

If you run hdparm manually, does it change the hard drive power management (parking) setting?

If so, (and the nohdparm kernel boot parameter doesn't work) you should be able to use the scripts in /etc/pm/power.d and /etc/pm/sleep.d.

Does the hdparm command work after resuming from sleep?

---

### Post by Toz on 2012-05-06
Just had a look at my /var/log/pm-suspend.log file. I got the execution order wrong. Try changing 99-hdparm-stop-disk-idling to 94-hdparm-stop-disk-idling.

Maybe also post back your /var/log/pm-powersave.log file so we can see if the execution is happening in the correct order.

---

### Post by jonnyboysmithy on 2012-05-06
> **Toz said:**
> After booting with the nohdparm kernel parameter, can you post back the results of:
```
cat /proc/cmdline
```If you run hdparm manually, does it change the hard drive power management (parking) setting?

If so, (and the nohdparm kernel boot parameter doesn't work) you should be able to use the scripts in /etc/pm/power.d and /etc/pm/sleep.d.

Does the hdparm command work after resuming from sleep?
The output:
> cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=01db9c4e-2027-441d-87eb-b3551612d557 ro acpi_backlight=vendor quiet splash nohdparm vt.handoff=7If I manually run: ```
sudo hdparm -B 255 /dev/sda
```That works as it should. I have a script that runs that at startup, that works.
Also when I run it manually it does work.

[B]
Log of: /var/log/pm-suspend.log
[/B]```
enabled, not active

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
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
Mon May  7 08:19:48 NZST 2012: Finished.
Initial commandline parameters: 
Mon May  7 09:51:53 NZST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux jotham-HP-Pavilion-dv6 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
i915                  468651  3 
uvcvideo               72627  0 
radeon                804372  0 
ttm                    76949  1 radeon
snd_hda_intel          33773  3 
drm_kms_helper         46978  2 i915,radeon
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12529  2 
drm                   242038  6 i915,radeon,ttm,drm_kms_helper
iwlwifi               328352  0 
snd_hwdep              13668  1 snd_hda_codec
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
psmouse                87692  0 
mei                    41616  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13423  2 i915,radeon
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rts_pstor             445196  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
serio_raw              13211  0 
wmi                    19256  1 hp_wmi
video                  19596  1 i915
mac_hid                13253  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
input_polldev          13896  1 lis3lv02d
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       8125004    1593228    6531776          0      82880     746816
-/+ buffers/cache:     763532    7361472
Swap:      2097148          0    2097148

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend: success.
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

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/hdparm-stop-disk-cycle-when-idle suspend suspend:

/etc/pm/sleep.d/hdparm-stop-disk-cycle-when-idle suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon May  7 09:51:54 NZST 2012: performing suspend
Mon May  7 14:22:11 NZST 2012: Awake.
Mon May  7 14:22:11 NZST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/hdparm-stop-disk-cycle-when-idle resume suspend:

/dev/sda:
 setting Advanced Power Management level to disabled
 APM_level    = off

/etc/pm/sleep.d/hdparm-stop-disk-cycle-when-idle resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
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
Mon May  7 14:22:12 NZST 2012: Finished.


```

---

### Post by Toz on 2012-05-06
Try changing the name of the file to 94-hdparm-stop-disk-idling - I think its a timing thing. The regular script is running after and re-setting it back.

---

### Post by jonnyboysmithy on 2012-05-07
Its working when I take out the power:P

But it still cycles (goes to powersave mode) when it comes back on from suspend.
I have changed it to 94-hdparm-stop-disk-idling

---

### Post by Toz on 2012-05-07
Hmmm. Try changing /etc/pm/sleep.d/94-hdparm-stop-disk-idling to /etc/pm/sleep.d/01-hdparm-stop-disk-idling. Can you also post back the contents of that file one more time so I can take a look?

---

### Post by jonnyboysmithy on 2012-05-08
I accidentally was changing the numbers on the wrong file in /power.d. I think we got the power.d bit right, because it doesn't cycle when unplugged or plugged in. Its only when it comes on from suspend that needs sorting.
So, I changed the /sleep.d script with 01 in front of it. And it still cycles after coming back from suspend.
Could it be a typo or error in the script you gave me?
This is what I have at the moment:
```
#!/bin/bash

case "${1}" in
    hibernate|suspend)
       # do nothing
       ;;
    resume|thaw)
       /sbin/hdparm -B 255 /dev/sda
       ;;
esac
```
```
enabled, not active

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
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
Wed May  9 09:11:06 NZST 2012: Finished.
Initial commandline parameters: 
Wed May  9 09:13:39 NZST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux jotham-HP-Pavilion-dv6 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
uas                    18027  0 
usb_storage            49198  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
radeon                804372  0 
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
i915                  468651  3 
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    76949  1 radeon
drm_kms_helper         46978  2 radeon,i915
drm                   242038  6 radeon,i915,ttm,drm_kms_helper
psmouse                87692  0 
iwlwifi               328352  0 
hp_accel               25976  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             445196  0 
lis3lv02d              19876  1 hp_accel
i2c_algo_bit           13423  2 radeon,i915
serio_raw              13211  0 
hp_wmi                 18092  0 
mac_hid                13253  0 
mac80211              506816  1 iwlwifi
mei                    41616  0 
input_polldev          13896  1 lis3lv02d
sparse_keymap          13890  1 hp_wmi
soundcore              15091  1 snd
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       8125004    3960376    4164628          0     148608    2521884
-/+ buffers/cache:    1289884    6835120
Swap:      2097148          0    2097148

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
'SUSPEND' command timed out.

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/99-hdparm-stop-disk-cycle-when-idle suspend suspend:

/etc/pm/sleep.d/99-hdparm-stop-disk-cycle-when-idle suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed May  9 09:13:45 NZST 2012: performing suspend
Wed May  9 09:13:55 NZST 2012: Awake.
Wed May  9 09:13:55 NZST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /etc/pm/sleep.d/99-hdparm-stop-disk-cycle-when-idle resume suspend:

/dev/sda:
 setting Advanced Power Management level to disabled
 APM_level    = off

/etc/pm/sleep.d/99-hdparm-stop-disk-cycle-when-idle resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
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
Wed May  9 09:13:56 NZST 2012: Finished.
Initial commandline parameters: 
Wed May  9 09:18:10 NZST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux jotham-HP-Pavilion-dv6 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
uas                    18027  0 
usb_storage            49198  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
radeon                804372  0 
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
i915                  468651  3 
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    76949  1 radeon
drm_kms_helper         46978  2 radeon,i915
drm                   242038  6 radeon,i915,ttm,drm_kms_helper
psmouse                87692  0 
iwlwifi               328352  0 
hp_accel               25976  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             445196  0 
lis3lv02d              19876  1 hp_accel
i2c_algo_bit           13423  2 radeon,i915
serio_raw              13211  0 
hp_wmi                 18092  0 
mac_hid                13253  0 
mac80211              506816  1 iwlwifi
mei                    41616  0 
input_polldev          13896  1 lis3lv02d
sparse_keymap          13890  1 hp_wmi
soundcore              15091  1 snd
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       8125004    3978272    4146732          0     148892    2530068
-/+ buffers/cache:    1299312    6825692
Swap:      2097148          0    2097148

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/01-hdparm-stop-disk-cycle-when-idle suspend suspend:

/etc/pm/sleep.d/01-hdparm-stop-disk-cycle-when-idle suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode suspend suspend: success.
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
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
Wed May  9 09:18:12 NZST 2012: performing suspend
Wed May  9 09:18:22 NZST 2012: Awake.
Wed May  9 09:18:22 NZST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend:

/usr/lib/pm-utils/sleep.d/01laptop-mode resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /etc/pm/sleep.d/01-hdparm-stop-disk-cycle-when-idle resume suspend:

/dev/sda:
 setting Advanced Power Management level to disabled
 APM_level    = off

/etc/pm/sleep.d/01-hdparm-stop-disk-cycle-when-idle resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed May  9 09:18:23 NZST 2012: Finished.
```

---

### Post by Toz on 2012-05-08
Hmmm - that should work. According to the log file, it did. Something must be re-enabling it later on down the road.

What happens if you rename the file to **/etc/pm/sleep.d/00a-hdparm-stop-disk-idling** to make it run later in the thaw sequence.

Do you have laptop-mode-tools installed:
```
apt-cache policy laptop-mode-tools
```

---

### Post by jonnyboysmithy on 2012-05-09
Yup, I do. I shall I remove those.
EDIT: I only removed the laptop-mode-tools, I didn't rename the file.
Seems to be ok now. Maybe that was it?

---

### Post by Toz on 2012-05-09
Thats what I was thinking. Something was unsetting the change that our script was making - laptop-mode-tools was a likely culprit.

---

### Post by jonnyboysmithy on 2012-05-09
And... I reinstallled it because otherwise it would think its on battery when the adapter is plugged in..

---

### Post by Toz on 2012-05-09
Look into its config file (or post it back here) and look or where the hard drive power management command is and disable it.

---

### Post by jonnyboysmithy on 2012-05-10
Mmm. I think I'll have to get better at reading these scripts, at the moment I find it difficult to read...
Anyway I think its this file: /usr/share/laptop-mode-tools/modules/hdparm 
EDIT: maybe I could comment out the whole script? :D
```

#! /bin/sh
#
# Laptop mode tools module: adjust hard drive powermanagement settings
#
# This is a core module that takes its configuration from the main config
# file.
#

#
# Function for drive capability check. This prevents ugly errors in
# the kernel output about unsupported commands.
#
# $1 = drive name
# $2 = capability (SDPARM/HDPARM or IDLE_TIMEOUT/POWERMGMT/WRITECACHE)
is_capable() {
    local dev=${1#/dev/}
    local MEDIA=
    local BUS=
    
    # Make sure the drive exists before checking anything.
    if ! [ -e $1 ]; then
        return 1;
    fi

    # If we are running udev, this is the most portable way
    # It assumes more or less recent udev (> 070)
    if [ $HAVE_UDEVINFO -ne 0 ] ; then
        log "VERBOSE" "Querying $1 media type using udevinfo: "
        if [ -x /sbin/udevadm ]; then
            eval "$(udevadm info -q env -n $1 | egrep '(ID_TYPE=|ID_BUS=)' )"
        else
            eval "$(udevinfo -q env -n $1 | egrep '(ID_TYPE=|ID_BUS=)' )"
        fi
        if [ -n "$ID_TYPE" -a -n "$ID_BUS" ] ; then
            log "VERBOSE" "type '$ID_TYPE' on bus '$ID_BUS' detected"
            MEDIA=$ID_TYPE
            BUS=$ID_BUS
        else
            log "ERR" "failed - udev not active?"
        fi
    fi

    if [ -z "$MEDIA" ] ; then
        log "VERBOSE" "Querying $1 media type using device name: "
        case $dev in
            hd*)    # IDE device
                if [ -r /proc/ide/$dev/media ]; then
                    MEDIA="$(cat /proc/ide/$dev/media)"
                    BUS=ata
                    if [ "$MEDIA" = cdrom ] ; then
                        MEDIA=cd
                    fi
                fi
            ;;
            sd*)    # SCSI disk
                # No need to check, sd is always SCSI disk
                MEDIA=disk
                BUS=scsi
            ;;
            sr* | scd* )
                # No need to check, sr or scd is always SCSI CD-ROM
                MEDIA=cd
                BUS=scsi
            ;;

        esac
        if [ -n "$MEDIA" ] ; then
            log "VERBOSE" "type '$MEDIA' on bus '$BUS' detected"
        else
            log "ERR" "failed - unknown name"
        fi
    fi

    if [ -z "$MEDIA" ] ; then
        if [ "$HDPARM_AVAILABLE" = "1" ]; then
            log "VERBOSE" "Querying $1 type using hdparm: "
            if hdparm -I $1 | grep -q CD-ROM ; then
                MEDIA=cd
            else
                MEDIA=disk
            fi
            BUS=ata # or acts like it anyway, because hdparm supports it.
            log "VERBOSE" "type '$MEDIA' on bus '$BUS' detected"
        fi
    fi

    # Sanity check
    if [ -z "$MEDIA" -o -z "$BUS" ] ; then
        log "ERR" "Querying $1 type - unknown type or bus, disabling hdparm/sdparm"
        return 1
    fi

    if [ "$BUS" = "scsi" -a "$ASSUME_SCSI_IS_SATA" -ne 0 ] ;then
        # Treat scsi disks as SATA devices. Unfortunately they are hard
        # to recognize -- if anybody has a drive and cares to find out
        # how to recognize them, please enlighten me!
        BUS=ata
    fi

    # Now check what capabilities we support for the
    # various media and bus types.
    case "$MEDIA:$BUS:$2" in
        # Although CD-ROM drives usually support
        # idle timeout settings, they don't usually
        # support very low values, and we don't want
        # to mess with that. We simply ignore anything
        # that is a CD player.
        cd:*:* ) return 1;;

        # ATA drives support the "hdparm" command but
        # not normally the "sdparm" command.
        *:ata:HDPARM ) return 0 ;;
        *:ata:SDPARM ) return 1 ;;
        
        # SCSI drives support the "sdparm" command, but
        # not normally the "hdparm" command.
        *:scsi:SDPARM ) return 0 ;;
        *:scsi:HDPARM ) return 1 ;;

        # On ATA disks everything is supported.
        disk:ata:* ) return 0 ;;

        # For sdparm we only know how to set the idle
        # timeout, nothing else at the moment.
        *:scsi:IDLE_TIMEOUT ) return 0 ;;

        # No other capabilities are supported.
        * ) return 1 ;;
    esac
}


# Preparation: determine the tools we have available.
if [ -x "$(which hdparm 2> /dev/null)" ]; then
  HDPARM_AVAILABLE=1
fi
if [ -x "$(which sdparm 2> /dev/null)" ]; then
  SDPARM_AVAILABLE=1
fi
HAVE_UDEVINFO=0
if [ -x "$(which udevadm 2> /dev/null)" ]; then
    UDEVVERSION=$(udevadm info -V)
    UDEV_VER_VERIFY=$(echo $UDEVVERSION | cut -b 1)
    case $UDEV_VER_VERIFY in
        [a-z]) UDEVVERSION=$(udevadm info -V | awk '{print $3}')
        ;;
        *)
        ;;
    esac

    if [ "$UDEVVERSION" -gt 70 ] ; then
        HAVE_UDEVINFO=1
    else
        log "VERBOSE" "udevadm info present but version not > 070, not using udev"
    fi
else
    # Older versions of udev (udevinfo) give output in the form of
    # "udevinfo, version 125"
    # Will be removed later. Currently only for backward compatibility
    if [ -x "$(which udevinfo 2> /dev/null)" ] ; then
        UDEVVERSION=$(udevinfo -V | awk '{ print $3; }')
        if [ "$UDEVVERSION" -gt 70 ] ; then
            HAVE_UDEVINFO=1
        else
            log "VERBOSE" "udevinfo present but version not > 070, not using udev"
        fi
    fi
fi

if [ x$CONTROL_HD_POWERMGMT = x1 ] || [ x$ENABLE_AUTO_MODULES = x1 -a x$CONTROL_HD_POWERMGMT = xauto ]; then
    if [ $ON_AC -eq 1 ] ; then
        if [ "$ACTIVATE" -eq 1 ] ; then
            HD_POWERMGMT=$LM_AC_HD_POWERMGMT
        else
            HD_POWERMGMT=$NOLM_AC_HD_POWERMGMT
        fi
    else
        HD_POWERMGMT=$BATT_HD_POWERMGMT
    fi

    log "VERBOSE" "Setting powermanagement on drives to $HD_POWERMGMT."
    for THISHD in $HD ; do
        if is_capable $THISHD POWERMGMT ; then
            if is_capable $THISHD HDPARM ; then
                if [ "$HDPARM_AVAILABLE" = "1" ]; then
                    log "VERBOSE" "Executing: hdparm -B $HD_POWERMGMT $THISHD"
                    log "VERBOSE" "`hdparm -B $HD_POWERMGMT $THISHD 2>&1`"
                else
                    log "ERR" "ERROR: hdparm not installed."                
                fi
            else
                log "VERBOSE" "Skipping $THISHD: powermgmt only possible with hdparm but drive does not"
                log "VERBOSE" "support hdparm."
            fi
        else
            log "VERBOSE" "Skipping $THISHD: powermanagement control not supported."
        fi
    done
fi

if [ x$CONTROL_HD_IDLE_TIMEOUT = x1 ] ; then
    # Spindown timeouts may only be set when data-loss sensitive
    # features are active.
    if [ "$ACTIVATE_WITH_POSSIBLE_DATA_LOSS" -eq 1 ] ; then
        if [ $ON_AC -eq 1 ] ; then
            HD_IDLE_TIMEOUT=$LM_AC_HD_IDLE_TIMEOUT
            HD_IDLE_TIMEOUT_SECONDS=$LM_AC_HD_IDLE_TIMEOUT_SECONDS
        else
            HD_IDLE_TIMEOUT=$LM_BATT_HD_IDLE_TIMEOUT
            HD_IDLE_TIMEOUT_SECONDS=$LM_BATT_HD_IDLE_TIMEOUT_SECONDS
        fi
    else
        HD_IDLE_TIMEOUT=$NOLM_HD_IDLE_TIMEOUT
        HD_IDLE_TIMEOUT_SECONDS=$NOLM_HD_IDLE_TIMEOUT_SECONDS
    fi
    log "VERBOSE" "Setting spindown timeout on drives to $HD_IDLE_TIMEOUT_SECONDS seconds."
    log "VERBOSE" "(hdparm configuration value = $HD_IDLE_TIMEOUT.)"
    for THISHD in $HD ; do
        if is_capable $THISHD IDLE_TIMEOUT ; then
            if is_capable $THISHD HDPARM ; then
                if [ "$HDPARM_AVAILABLE" = "1" ]; then
                    log "VERBOSE" "Executing: hdparm -S $HD_IDLE_TIMEOUT $THISHD"
                    log "VERBOSE" "`hdparm -S $HD_IDLE_TIMEOUT $THISHD 2>&1`"
                else
                    log "VERBOSE" "ERROR: hdparm not installed."
                fi
            elif is_capable $THISHD SDPARM ; then
                if [ "$SDPARM_AVAILABLE" = "1" ]; then
                    HD_IDLE_TIMEOUT_DECISECONDS=$(($HD_IDLE_TIMEOUT_SECONDS*10))
                    log "VERBOSE" "Executing: sdparm -q -s SCT=$HD_IDLE_TIMEOUT_DECISECONDS $THISHD"
                    log "VERBOSE" "`sdparm -q -s SCT=$HD_IDLE_TIMEOUT_DECISECONDS $THISHD 2>&1`"
                else
                    log "ERR" "ERROR: sdparm not installed."
                fi
            else
                log "VERBOSE" "Skipping $THISHD: drive supports neither hdparm nor sdparm."
            fi
        else
            log "VERBOSE" "Skipping $THISHD: idle timeout control not supported."
        fi
    done
fi

if [ x$CONTROL_HD_WRITECACHE = x1 ] ; then
    # The writecache may only be enabled when data-loss sensitive
    # features are active.

    if [ "$ACTIVATE" -eq 1 ] ; then
        if [ "$ACTIVATE_WITH_POSSIBLE_DATA_LOSS" -eq 0 ] ; then
            HD_WRITECACHE=0
        else
            HD_WRITECACHE=$LM_HD_WRITECACHE
        fi
    else
        if [ $ON_AC -eq 1 ] ; then
            HD_WRITECACHE=$NOLM_AC_HD_WRITECACHE
        else
            HD_WRITECACHE=$NOLM_BATT_HD_WRITECACHE
        fi
    fi
    log "VERBOSE" "Setting write cache on drives to $HD_WRITECACHE."
    for THISHD in $HD ; do
        if is_capable $THISHD WRITECACHE ; then
            if is_capable $THISHD HDPARM ; then
                if [ "$HDPARM_AVAILABLE" = "1" ]; then
                    log "VERBOSE" "Executing: hdparm -W $HD_WRITECACHE $THISHD"
                    log "VERBOSE" "`hdparm -W $HD_WRITECACHE $THISHD 2>&1`"
                else
                    log "ERR" "ERROR: hdparm not installed."
                fi
            else
                log "VERBOSE" "Skipping $THISHD: writecache only possible with hdparm but drive does not"
                log "VERBOSE" "support hdparm."
            fi
        else
            log "VERBOSE" "Skipping $THISHD: writecache control not supported."
        fi
    done
fi

```

---

### Post by Toz on 2012-05-10
Just downloaded the package and had a look. From the file: **/etc/laptop-mode/laptop-mode.conf**, we have these options:

> 
# Should laptop mode tools control the hard drive power management settings?
#
# Set to 0 to disable
CONTROL_HD_POWERMGMT="auto"


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254

You can either fine-tune the settings (I think you want to set all the values to 255) or disable the hd powersave feature by simply changing CONTROL_HD_POWERMGMT to:
```
CONTROL_HD_POWERMGMT=0
```

You'll need to restart laptop-mode-tools to re-read the config file. It might be something like this:
```
sudo service laptop-mode restart
```

---

### Post by jonnyboysmithy on 2012-05-11
Seems to have done the trick!
 If, lol if it starts cycling I'll post back here  :D.

---

### Post by Toz on 2012-05-11
Glad to head. Can you please mark this thread as solved from the "Thread Tools" link above?

---

### Post by jonnyboysmithy on 2012-05-11
> **Toz said:**
> Glad to head. Can you please mark this thread as solved from the "Thread Tools" link above?
Sure.

Thank you for helping me out even though it took so long:KS 
and may many others help you as you have helped me.


Greetings, Jotham

---

