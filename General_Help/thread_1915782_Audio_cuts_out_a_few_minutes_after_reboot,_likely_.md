---
title: "Audio cuts out a few minutes after reboot, likely ALSA problem: Ubuntu 11.10"
date: 2012-01-26
forum: General Help
---

### Post by rybu on 2012-01-26
Hi everyone, 

I installed Ubuntu 11.10 in November on my laptop (and office computer) and it's been mostly running fine.  But about three weeks ago, after an upgrade some new behaviour has been occuring. 

After I turn on the computer, everything is fine for the first 5 minutes, maybe even up to an hour.  But after some point, the audio stops.  

If I run an application that should produce sound, the application "pavucontrol" will show it on its audio monitor.  I've tried re-loading alsa as in this thread: [http://ubuntuforums.org/showthread.php?t=1894231](http://ubuntuforums.org/showthread.php?t=1894231) and reinstalling the audio base as in this thread: [http://ubuntuforums.org/showthread.php?t=1746855](http://ubuntuforums.org/showthread.php?t=1746855) but none of them have had any noticable affect. 

Similarly, running gstreamer-properties with the settings suggested by lidex here: [http://ubuntuforums.org/showthread.php?t=1725874&page=4](http://ubuntuforums.org/showthread.php?t=1725874&page=4) makes no difference. 

output from: sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

```

[sudo] password for rybu: 
Cannot stat /dev/dsp*: Bad address
Cannot stat /dev/seq*: Bad address
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  rybu       2291 F.... pulseaudio
/dev/snd/seq:        timidity   1934 F.... timidity

```

and:

perhaps the more interesting output:

```

E: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
E: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

```

this is from running the command: pkill pulseaudio; sleep 2; pulseaudio -vv

The forum chokes on the complete output -- it's quite long. Any ideas?  It kind of looks like an ALSA problem.  But what's the problem?

Some relevant output: 

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

and

```
cat /etc/pulse/daemon.conf 
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
; deferred-volume-safety-margin-usec = 8000
; deferred-volume-extra-delay-usec = 0

```

```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2620000 irq 45
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6MHT43WW-1.18

```

---

### Post by rybu on 2012-01-27
I've made some progress on this problem.  I haven't resolved it, but here's some progress.  It appears that a possible contributing factor in the problem is some unresolved dependencies that were introduced when I upgraded my laptop from 11.04 to 11.10.  I ran aptitude shortly after posting this thread and discovered them.  There were a bunch of i386 modules installed, some to do with ALSA.  After resolving the dependencies (including uninstalling over 20 applications) various things like the sound indicator applet were missing, so I had to re-install them, and flashplayer, strangely enough.   The output to the above commands have changed too.  But the problem with the sound cutting out after a few minutes has not. 

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Cannot stat /dev/dsp*: Bad address
Cannot stat /dev/seq*: Bad address
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  rybu       2251 F.... pulseaudio
/dev/snd/pcmC0D0p:   rybu       2251 F...m pulseaudio
/dev/snd/seq:        timidity   1816 F.... timidity

```

same as before: pkill pulseaudio; sleep 2; pulseaudio -vv

```

...
E: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
E: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
...

```

same as before:

 lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)


cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2620000 irq 44
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6MHT43WW-1.18

---

### Post by rybu on 2012-01-27
Some further data. 

sudo lshw -C multimedia

```

  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:f2620000-f2623fff

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

... found the audio troubleshooting guide and am working through it: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
```

Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

Produces no sound...

Okay, so I've been through the entire troubleshooting guide with no progress. :(

---

### Post by rybu on 2012-01-29
Progress!

The instructions given by Mhazen, in post 9 of this thread helps. 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/382440](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/382440)

I don't understand why it works, but it works!  Unfortunately, it's temporary.  Sound still cuts out, but I no longer have to reboot to get the sound working again.  Reloading ALSA seems to suffice, for 10 minutes or so.  Then I have to do it again. :(

Reloading ALSA seems to work for a short while, but after a bit I start getting problems like this, and ALSA won't reload: 

```

sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hrtimer snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hrtimer snd-seq snd-timer snd-seq-device).
Loading ALSA sound driver modules: snd-hrtimer snd-seq snd-timer snd-seq-device.

```

---

### Post by rybu on 2012-02-03
Today I tried reinstalling everything related to ALSA and Pulse.  I did an Synaptic search for all installed packages with those words in their descriptions, I think I reinstalled 25 or so packages.  

Makes no difference.  Sigh.    When you do a reinstall via Synaptic does it completely rewrite the old configuration files, or does it try to maintain the old configurations?   I wonder if there's something it misses.   Complete removal looked dangerous as there were a lot of other packages that would have had to be removed, I wasn't certain if that would be safe.

Created a bug report in launchpad: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/925910](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/925910)

And after the upgrade to 12.04, the problem persists. :(

---

### Post by rybu on 2012-05-01
The problem isn't as bad in 12.04.    It takes hours before the sound cuts out.  And if I run:

pulseaudio --kill
sudo alsa force-reload
pulseaudio --start

in that order, I seem to get at least another hour of sound.

---

### Post by rybu on 2012-05-14
I'm starting to think it's a hardware problem, not a software program. 

After the sound cut out I connected my bluetooth headphones to the laptop, and configured the laptop so that all sound went through the headphones.  Headphone audio works perfectly when the laptop speaker has cut out. 

What would Ubuntu to have it "give up" on the laptop speaker this way?  

With the laptop configured to use the laptop speaker for audio, after it cuts out I can run:

pulseaudio --kill
sudo alsa force-reload
pulseaudio --start

and it will work... for a while.  So it almost has the behavior of a blown fuse, and the above pulseaudio/alsa cycle is like resetting the breaker/fuse.

---

