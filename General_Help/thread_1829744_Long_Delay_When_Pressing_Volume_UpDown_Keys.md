---
title: "Long Delay When Pressing Volume Up/Down Keys"
date: 2011-08-20
forum: General Help
---

### Post by Joseph Schwenker on 2011-08-20
I've been having a problem when my computer starts up with my volume up and down multimedia keys. When I press them, the volume is not changed until a minute or two later, even though I can adjust the volume from its applet during the time when the keys do nothing. I had this issue in Ubuntu 10.10, and I'm still having it in 11.04. Anyone know what could be causing the problem?

---

### Post by Script Warlock on 2011-08-22
when adjusting the volume did you sense the sound also delays or only the notification.

---

### Post by Joseph Schwenker on 2011-08-23
> **Script Warlock said:**
> when adjusting the volume did you sense the sound also delays or only the notification.

The sound also delayed, and all the times I'd hit the button without it registering added up, so I'd get spammed by the volume randomly turning down or up whenever the OS decided to finally register the keys.

---

### Post by Joseph Schwenker on 2011-08-24
Interestingly, the issue seems to go like this:

I turn on my computer, and Banshee starts up as a start up application. I can adjust the volume now.
I choose a song to start playing. I can still adjust the volume and use my media keys.
I launch the other applications that I need (Chrome, Empathy, Skype, Evolution, and my Downloads folder), and can still adjust the volume.
For an arbitrary reason, I decide I want to turn the volume down or pause playback. However, at this point, the volume and media keys stop responding, and a minute later, all of the keys I pressed are registered at once, leading to eardrum-shattering results.

---

### Post by Joseph Schwenker on 2011-08-27
Issue still persists, even outside of Banshee. Could it be something with my BIOS? I can adjust the volume level from the volume control applet, but not with my multimedia keys.

---

### Post by Joseph Schwenker on 2011-08-31
The problem might be with Banshee, because while the keys weren't being registered, I tried closing Banshee, but it froze. After I xkilled it, my keys immediately started registering again. It might be Banshee's multimedia keys extension.

UPDATE: I disabled Docky's Banshee helper, and I also enabled the MPRIS D-Bus Interface extension, and things *seem* to be fine now. I'll keep my ears open for any more problems over the next few days.

---

### Post by Joseph Schwenker on 2011-09-04
Issue still persists. Interestingly, when I use xkill to kill Banshee by clicking on its GUI, it still plays music. I have to kill it from command line with killall -9 banshee. After I kill it, keyboard volume input still isn't registered. When I open Banshee again, its volume control button is grayed out, and it won't play any songs.
I'll try going after PulseAudio next.

---

### Post by Joseph Schwenker on 2011-09-12
Could the problem be with the ibus-daemon zombie process? I have killall -9 ibus-daemon in my startup applications, because it interferes with many games, and I don't use it that often.

---

### Post by Joseph Schwenker on 2011-09-21
Interestingly enough, when I press the volume up/down media keys, the focus is changed from the current window, just as happens when volume adjustment works normally. However, during the period when these keys do not register, no notification bubble pops up and the volume does not change, despite the focus changing.

---

### Post by hakermania on 2011-09-30
Hey, I am just curious If you can confirm this:
[https://bugs.launchpad.net/notify-osd/+bug/841279](https://bugs.launchpad.net/notify-osd/+bug/841279)
Good to insist :) You will soon reach 1 million bumps, this will be a record!

---

### Post by Joseph Schwenker on 2011-10-01
I took a look at that bug, but it doesn't describe my problem. My problem happens with Banshee, and happens both when it's running and when it's not running. Also, the problem doesn't go away when I close Banshee (Banshee and Totem won't close unless I force quit them, actually).

---

### Post by Slim Odds on 2011-10-10
> **Joseph Schwenker said:**
> bump

Have these bumps been helpful at getting you an answer?

NO

---

### Post by Joseph Schwenker on 2011-10-13
I timed the time during which my multimedia keys did not respond today. It took approximately four minutes for them to start responding again.

---

### Post by Slim Odds on 2011-10-13
> **Joseph Schwenker said:**
> I timed the time during which my multimedia keys did not respond today. It took approximately four minutes for them to start responding again.

Wow, that's WAY too long.

With 10.04, sometimes I had a few seconds delay. But nothing like what you're seeing.

---

### Post by mutley89 on 2011-12-10
Impressive pesistance :)  
I have no idea what your problem is or how to solve it, However as a possible workaround how long does the following take:
```
pactl set-sink-volume 0 10000
```The last number is your volume level, try adjusting it.  i'm not sure if this will work as is with difffering setups, if not post the output of "pacmd dump".  If this works it's easy to construct a script to do it incrementally.

---

### Post by Joseph Schwenker on 2011-12-11
> **mutley89 said:**
> Impressive pesistance :)  
I have no idea what your problem is or how to solve it, However as a possible workaround how long does the following take:
```
pactl set-sink-volume 0 10000
```The last number is your volume level, try adjusting it.  i'm not sure if this will work as is with difffering setups, if not post the output of "pacmd dump".  If this works it's easy to construct a script to do it incrementally.

I tried the first command, and the results were instant, even when multimedia keys were unresponsive.

I ran the second command twice, once during the unresponsive time and once afterwards.

During:

```
Welcome to PulseAudio! Use "help" for usage information.
>>> ### Configuration dump generated at Sun Dec 11 09:14:15 2011

load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore
load-module module-augment-properties
load-module module-alsa-card device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
load-module module-alsa-card device_id="1" name="usb-046d_089d-01-U0x46d0x89d" card_name="alsa_card.usb-046d_089d-01-U0x46d0x89d" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
load-module module-udev-detect
load-module module-bluetooth-discover
load-module module-esound-protocol-unix
load-module module-native-protocol-unix
load-module module-gconf
load-module module-default-device-restore
load-module module-rescue-streams
load-module module-always-sink
load-module module-intended-roles
load-module module-suspend-on-idle
load-module module-console-kit
load-module module-position-event-sounds
load-module module-x11-publish display=:0
load-module module-x11-bell display=:0 sample=bell.ogg
load-module module-x11-cork-request display=:0
load-module module-x11-xsmp display=:0 session_manager=local/joseph:@/tmp/.ICE-unix/1768,unix/joseph:/tmp/.ICE-unix/1768
load-module module-cli-protocol-unix

set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo 0x2710
set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo no
suspend-sink alsa_output.pci-0000_00_1b.0.analog-stereo yes

set-source-volume alsa_output.pci-0000_00_1b.0.analog-stereo.monitor 0x10000
set-source-mute alsa_output.pci-0000_00_1b.0.analog-stereo.monitor no
suspend-source alsa_output.pci-0000_00_1b.0.analog-stereo.monitor yes
set-source-volume alsa_input.pci-0000_00_1b.0.analog-stereo 0x4c6d
set-source-mute alsa_input.pci-0000_00_1b.0.analog-stereo no
suspend-source alsa_input.pci-0000_00_1b.0.analog-stereo yes
set-source-volume alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono 0x69b3
set-source-mute alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono no
suspend-source alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono yes

set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-stereo+input:analog-stereo
set-card-profile alsa_card.usb-046d_089d-01-U0x46d0x89d input:analog-mono

set-default-sink alsa_output.pci-0000_00_1b.0.analog-stereo
set-default-source alsa_input.pci-0000_00_1b.0.analog-stereo

### EOF
>>> 
```

After:

```
Welcome to PulseAudio! Use "help" for usage information.
>>> ### Configuration dump generated at Sun Dec 11 09:18:47 2011

load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore
load-module module-augment-properties
load-module module-alsa-card device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
load-module module-alsa-card device_id="1" name="usb-046d_089d-01-U0x46d0x89d" card_name="alsa_card.usb-046d_089d-01-U0x46d0x89d" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"
load-module module-udev-detect
load-module module-bluetooth-discover
load-module module-esound-protocol-unix
load-module module-native-protocol-unix
load-module module-gconf
load-module module-default-device-restore
load-module module-rescue-streams
load-module module-always-sink
load-module module-intended-roles
load-module module-suspend-on-idle
load-module module-console-kit
load-module module-position-event-sounds
load-module module-x11-publish display=:0
load-module module-x11-bell display=:0 sample=bell.ogg
load-module module-x11-cork-request display=:0
load-module module-x11-xsmp display=:0 session_manager=local/joseph:@/tmp/.ICE-unix/1768,unix/joseph:/tmp/.ICE-unix/1768
load-module module-cli-protocol-unix

set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo 0x6480
set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo no
suspend-sink alsa_output.pci-0000_00_1b.0.analog-stereo no

set-source-volume alsa_output.pci-0000_00_1b.0.analog-stereo.monitor 0x10000
set-source-mute alsa_output.pci-0000_00_1b.0.analog-stereo.monitor no
suspend-source alsa_output.pci-0000_00_1b.0.analog-stereo.monitor no
set-source-volume alsa_input.pci-0000_00_1b.0.analog-stereo 0x4c6d
set-source-mute alsa_input.pci-0000_00_1b.0.analog-stereo no
suspend-source alsa_input.pci-0000_00_1b.0.analog-stereo yes
set-source-volume alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono 0x69b3
set-source-mute alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono no
suspend-source alsa_input.usb-046d_089d-01-U0x46d0x89d.analog-mono yes

set-card-profile alsa_card.pci-0000_00_1b.0 output:analog-stereo+input:analog-stereo
set-card-profile alsa_card.usb-046d_089d-01-U0x46d0x89d input:analog-mono

set-default-sink alsa_output.pci-0000_00_1b.0.analog-stereo
set-default-source alsa_input.pci-0000_00_1b.0.analog-stereo

### EOF
>>> 
```

---

### Post by mutley89 on 2011-12-11
From the Arch wiki, put this in a file called "~/bin/pulse-volume" and "chmod +x" it:
```

#!/bin/bash
device="alsa_output.pci-0000_00_1b.0.analog-stereo"
case "$1" in
    "up")    # increase volume by 1000
        pacmd dump | awk --non-decimal-data '$1~/set-sink-volume/{if ($2~/'${device}'/) {if ($3+1000 > 65535) {system ("pactl "$1" '${device}' "65535)} else {system ("pactl "$1" '${device}' "$3+1000)}}}'
        ;;
    "down")  # decrease volume by 1000
        pacmd dump | awk --non-decimal-data '$1~/set-sink-volume/{if ($2~/'${device}'/) {if ($3-1000 < 0) {system ("pactl "$1" '${device}' "0)} else {system ("pactl "$1" '${device}' "$3-1000)}}}'
        ;;
    "mute")  # toggle mute
        pacmd dump|awk --non-decimal-data '$1~/set-sink-mute/{if ($2~/'${device}'/) {system ("pactl "$1" '${device}' "($3=="yes"?"no":"yes"))}}'
        ;;
esac

```If you don't already have the ~/bin directory run ". ~/.profile" to include it in your PATH.

Then change the keyboard shortcuts defined for your volume keys to "pulse-volume up", pulse-volume down" and "pulse-volume mute" as appropriate.  This should allow you to change the volume through the keys, however it won't give you any visual feedback.

Before you do that however, if you run "top" in a terminal and then press the volume keys, does any process shoot up?

---

### Post by Joseph Schwenker on 2011-12-13
> **mutley89 said:**
> Before you do that however, if you run "top" in a terminal and then press the volume keys, does any process shoot up?

I have quite the interesting report for you regarding that. When the keys are responding, Xorg jumps up to the top of the list. However, I've found that just before the keys stop responding, tracker-store's CPU usage spirals up like crazy. After the keys stopped responding, I tried killing tracker-store to see if it would fix the problem. It did not. However, the next highest item on the list was gnome-settings-daemon, which was uninterruptible (sync_page) while the keys were not responding. After I killed it, nothing happened, until I killed tracker-store a second time. The keys started responding after this, though this could just be a coincidence.
I retried killing tracker-store, gnome-settings-daemon, tracker-store the next day, and the results were reproduced, though the keys became unresponsive again after a while.

---

### Post by Joseph Schwenker on 2011-12-20
I've continued to try killing gnome-settings-daemon and tracker-store, and it seems to fix the problem invariably, though only temporarily, as the problem re-appears later.
This is not a solution to the problem, however.

---

### Post by Joseph Schwenker on 2011-12-25
I've investigated further into the whole tracker-store gnome-settings-daemon thing, and I've found that tracker-store may not have anything to do with the problem; only gnome-settings-daemon. If I killall -9 gnome-settings-daemon then run gnome-settings-daemon again, I am invariably able to use my volume up/down keys as well as all other media keys. However, as I reported before, the fix lasts only for a few minutes before media keys stop responding again. However, killing and relaunching gnome-settings-daemon at this point will still invariably fix the problem, albeit still temporarily.

---

### Post by Joseph Schwenker on 2012-01-01
This problem is almost certainly related to gnome-settings-daemon, and it's given me trouble before with different problems. Is there any way to get debug output from gnome-settings-daemon on startup?

---

### Post by Joseph Schwenker on 2012-01-15
The problem is almost certainly with gnome-settings-daemon, and I even found multimedia key bindings in Gconf under apps, gnome_settings_daemon. I tried killing and restarting gnome-settings-daemon, but no output is produced when the process becomes uninterruptible.

---

### Post by Joseph Schwenker on 2012-01-20
I was searching around about my problem today, and I happened to come across [this bug]("https://bugs.launchpad.net/gnome-settings-daemon/+bug/505085"). Initially, I didn't believe it to be related to my problem, but some of the symptoms seemed to fit.

Users affected by the bug seemed to mention ~.thumbnails a lot, so I opened up that directory and moved it to my desktop. Instantly, gnome-settings-daemon started responding again. Coincidence? I think not.

Furthermore, I analyzed the contents of the folder with Disk Usage Analyzer, and I found that the entire thumbnails directory totaled a whopping 880MB!

Moving/deleting the thumbnails directory might just solve the problem. I'll post later with further findings.

---

### Post by Joseph Schwenker on 2012-01-22
Deleting ~.thumbnails seems to have nearly solved the problem. Though gnome-settings-daemon still becomes uninterruptible, it does so for a much shorter time span than previously (just a few seconds, as opposed to several minutes).

Since this is more of a bug with gnome-settings-daemon than a support question, and since I've pretty much solved the problem to my satisfaction, I'll be marking this thread as solved.

Thanks for your help, everyone!

---

