---
title: "run script in startup"
date: 2010-12-02
forum: General Help
---

### Post by cobra11 on 2010-12-02
When i use two finger tap touchap knows like it is middle click. How to get this code permanetly used when i boot in linux or after suspend/hibernate?

```
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 2, 3, 0, 0, 1, 2, 3
```

---

### Post by searchfgold6789 on 2010-12-02
Make it executable```
chmod +x <filename>
```and then put it in the /etc/init.d directory. :)

---

### Post by cobra11 on 2010-12-02
Nothing woork, like it wont load this script...

---

### Post by cobra11 on 2010-12-02
I want to make xinput setting permanent but ****n dont know how.. Try a lot of things but after reboot settings restart. Like OS ignore my script,any ideas how to fix it?

---

### Post by lrgmmc on 2010-12-02
from terminal ```
sudo nano /etc/init.d/testmouse
```
then add ```

#! /bin/bash
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 2, 3, 0, 0, 1, 2, 3
```
 
then ctrl + x to exit. it will ask if you want to save type y.
after it is saved type ```
sudo chmod +x /etc/init.d/testmouse
sudo update-rc.d testmouse defaults
```
then reboot and it should work.

---

### Post by searchfgold6789 on 2010-12-02
Maybe make a button that runs the script on your desktop from the terminal?
Not ideal but it would work...

---

### Post by cobra11 on 2010-12-02
Still nothing works... 
Nah i dont want to have button and than anytime when i suspend or hibernate i must click it..

---

### Post by lrgmmc on 2010-12-02
give this a look and see if it help [https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

---

### Post by cobra11 on 2010-12-02
I try this from begin but that isnt working too...
Anyone else have some ideas how to make middleclick permanent on two tap finger press?

---

### Post by cobra11 on 2010-12-03
Soo anyone have idea how to fix it?

---

### Post by lrgmmc on 2010-12-03
so here goes. i tried this a few times seams to work.
 
```

sudo touch /etc/pm/sleep.d/99-touchpad.sh
sudo chmod +x /etc/pm/sleep.d/99-touchpad.sh
sudo nano /etc/pm/sleep.d/99-touchpad.sh
```
 
then add
```

#!/bin/bash
case "$1" in
    thaw|resume)
        /etc/init.d/touchpad 2>/dev/null
        ;;
    *)
        ;;
esac
exit $?
```
 
then 
 
```
sudo touch /etc/init.d/touchpad
sudo chmod +x /etc/init.d/touchpad
sudo nano /etc/init.d/touchpad
```
 
add
 
```

#! /bin/sh
/bin/sh -c `DISPLAY=:0 xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 2, 3, 0, 0, 1, 2, 3 &`
```
now open and add this to the end of .profile
 
```
nano ~/.profile
 
/etc/init.d/touchpad &

```
 
that should get it all working.

---

### Post by cobra11 on 2010-12-03
I doo like you said but still nothing seems to work :O...
If i run scrip touchpad from terminal normaly work if i suspend or hibernate nothing works again.. If i run 99 touchpad.. again nothing works.. Am i doing something wrong or is something wrong with my OS or what?

---

### Post by lrgmmc on 2010-12-03
re look at what i wrote i edited it like a minute ago.
there was a typo sudo nano /etc/pm/sleep.d/99-touchpad should have been sudo nano /etc/pm/sleep.d/99-touchpad.sh
i already changed the post.

---

### Post by cobra11 on 2010-12-03
I do everything like you said but still nothing works i add i .profile at the end but like i said nothing seems to work..

---

### Post by cobra11 on 2010-12-03
Still nothing...

---

### Post by lrgmmc on 2010-12-03
try rebooting.

---

### Post by cobra11 on 2010-12-03
I try everything,rebooting,suspending,hibernatiog,logging out and soo on but as i said nothing can get this script work..
Is this script working for you?

---

### Post by lrgmmc on 2010-12-03
yes on reboot not on resum. i am working on resum right now.
try running ```
/etc/init.d/touchpad

```
anything?

---

### Post by cobra11 on 2010-12-03
It works if i write this in terminal..

---

### Post by lrgmmc on 2010-12-03
ok so run this ```
sudo rm /var/log/pm-suspend.log
sudo touch /var/log/pm-suspend.log
```
then suspend and resume.
then post back the contents of this file
```
sudo nano /var/log/pm-suspend.log
```

---

### Post by cobra11 on 2010-12-03
This is what i get:

Initial commandline parameters: 
Fri Dec  3 17:36:06 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux peter-UL30VT 2.6.35-23-generic-pae #40-Ubuntu SMP Wed Nov 17 22:32:51 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
parport_pc             26378  0 
ppdev                   5556  0 
rfcomm                 33811  0 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  6 rfcomm,bnep
vboxnetadp              6454  0 
vboxnetflt             15216  0 
snd_hda_codec_nvhdmi    13615  4 
vboxdrv               190135  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   217971  1 
arc4                    1165  2 
joydev                  8735  0 
snd_hda_intel          22203  2 
iwlagn                179815  0 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
nouveau               517660  0 
snd_hwdep               5040  1 snd_hda_codec
snd_seq_midi            4588  0 
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            17783  1 snd_seq_midi
i915                  293387  3 
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56825  1 nouveau
iwlcore               127479  1 iwlagn
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  2 nouveau,i915
mac80211              231541  2 iwlagn,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
btusb                  11001  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              50500  7 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               55911  0 
drm                   168726  6 nouveau,ttm,i915,drm_kms_helper
intel_agp              26784  2 i915
asus_laptop            14084  0 
cfg80211              144470  3 iwlagn,iwlcore,mac80211
videodev               43098  1 uvcvideo
sparse_keymap           3145  1 asus_laptop
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  1 asus_laptop
i2c_algo_bit            5168  2 nouveau,i915
video                  18712  1 i915
acpi_call               3719  0 
psmouse                59033  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
output                  1883  1 video
agpgart                32075  3 ttm,drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
libahci                21731  4 ahci
             total       used       free     shared    buffers     cached
Mem:       4082340    1229440    2852900          0     272988     571900
-/+ buffers/cache:     384552    3697788
Swap:      3320828          0    3320828

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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.1 -> dest=:1.145 reply_serial=2
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
Running hook /etc/pm/sleep.d/99-disable-nvidia.sh suspend suspend:

/etc/pm/sleep.d/99-disable-nvidia.sh suspend suspend: success.
Running hook /etc/pm/sleep.d/99-touchpad.sh suspend suspend:

/etc/pm/sleep.d/99-touchpad.sh suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/asus-bluetooth suspend suspend:

/etc/pm/sleep.d/asus-bluetooth suspend suspend: success.
Fri Dec  3 17:36:07 CET 2010: performing suspend
Fri Dec  3 17:36:15 CET 2010: Awake.
Fri Dec  3 17:36:15 CET 2010: Running hooks for resume
Running hook /etc/pm/sleep.d/asus-bluetooth resume suspend:

/etc/pm/sleep.d/asus-bluetooth resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /etc/pm/sleep.d/99-touchpad.sh resume suspend:

/etc/pm/sleep.d/99-touchpad.sh resume suspend: success.
Running hook /etc/pm/sleep.d/99-disable-nvidia.sh resume suspend:
Trying \_SB.PCI0.P0P1.VGA._OFF: works!

/etc/pm/sleep.d/99-disable-nvidia.sh resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa resume suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.1 -> dest=:1.149 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
Fri Dec  3 17:36:18 CET 2010: Finished.

---

### Post by cobra11 on 2010-12-05
Anybody have some ideas how to get it work?

---

