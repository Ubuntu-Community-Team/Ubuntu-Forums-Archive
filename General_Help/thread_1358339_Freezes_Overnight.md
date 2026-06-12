---
title: "Freezes Overnight"
date: 2009-12-18
forum: General Help
---

### Post by thomashw on 2009-12-18
For the last 3 nights in a row, when I go on my computer in the morning, it's completely frozen. The screen turns on and I can see everything, but it's totally unresponsive and I'm having to restart the computer.

It hasn't happened to me while I use the computer, just when I leave it for a long time (overnight.)

Any ideas? Any logs I should check (where)?

---

### Post by northern lights on 2009-12-18
/var/log/syslog

---

### Post by thomashw on 2009-12-18
This error constantly repeats:

> Dec 18 07:26:01 thomas-desktop pulseaudio[22222]: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:1,0"): initialization failed.
Dec 18 07:26:01 thomas-desktop pulseaudio[22222]: main.c: Module load failed.
Dec 18 07:26:01 thomas-desktop pulseaudio[22222]: main.c: Failed to initialize daemon.
Dec 18 07:26:01 thomas-desktop pulseaudio[22220]: main.c: Daemon startup failed.

Obviously it's something to do with pulse audio. Any idea what I can do to fix it?

---

### Post by northern lights on 2009-12-18
About that error: Have you recently removed a sound card, disabled one in the BIOS, own a USB headset, or similar?
```
device=hw:1,0
```is a secondary sound device - possibly pulseaudio is looking for a device not present (anymore).

However, this should not make your PC freeze. Especially not if occuring regularly. Check the times. Does the error not occur while the machine's up and unfrozen?!

---

### Post by thomashw on 2009-12-18
> **northern lights said:**
> About that error: Have you recently removed a sound card, disabled one in the BIOS, own a USB headset, or similar?
```
device=hw:1,0
```is a secondary sound device - possibly pulseaudio is looking for a device not present (anymore).

However, this should not make your PC freeze. Especially not if occuring regularly. Check the times. Does the error not occur while the machine's up and unfrozen?!
Hmm... no, I haven't done anything with any sound devices.

The error constantly loops, so yes it occurs when my PC isn't frozen. There are thousands of entries for the error in that log file.

P.S. The computer just froze again. Completely unresponsive.

---

### Post by northern lights on 2009-12-18
I don't see how pulseaudio could regularly freeze your system completely, but not every time on occurence of the error.

However, the two might very well be connected.

Run```
gksu gedit /etc/pulse/system.pa
```and check for this line```
load-module-alsa-source
```If it's there, comment it (put a hash/pound/# sign in front of it), restart and check whether the error seized occuring. If so, hope your system also seizes freezing. If it still does, we at least know that the suspected causal relationship had never been.

---

### Post by thomashw on 2009-12-18
That entry doesn't exist in that file.

I don't use sound much obviously, but I've just noticed the sound icon isn't showing anymore, and when I go "System -> Preferences -> Sound" it says "Waiting for sound system to respond" and just keeps waiting.

Any ideas?

---

### Post by thomashw on 2009-12-18
So I've been reading on the PulseAudio wiki, and it mentioned you can either specify the hardware or have it detected. So I opened the default.pa file and commented out the lines:

> ### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below — for doing this automatically)
###load-module module-alsa-sink
###lload-module module-alsa-source device=hw:1,0
###lload-module module-oss device=”/dev/dsp” sink_name=output source_name=input
###lload-module module-oss-mmap device=”/dev/dsp” sink_name=output source_name=input
###lload-module module-null-sink
###lload-module module-pipe-sink

and un-commented these:

> ### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-udev-detect
.endif

The error has stopped repeating itself, which is good! "Internal Audio Analog Stereo" is being detected. Is this right?

I don't have a dedicated sound card - just the one on my motherboard, so I'm not sure.

I'll leave my computer on for a while and see if it freezes or not.

---

### Post by pricetech on 2009-12-18
You mention "overnight" as when it freezes.  Any temperature changes in the room that occur at night ??

I bring this up because of a hardware problem I had many years ago with those exact symptoms.  Turned out to be a cold solder joint on the mobo and would fail at night when the temp dropped in my shop.

---

### Post by thomashw on 2009-12-18
Nope, the computer stays in my house and stays at a pretty constant temperature.

---

### Post by thomashw on 2009-12-19
Well, just got back to the computer and it didn't freeze all day!

I'm going to leave it overnight. I'll report back.

---

