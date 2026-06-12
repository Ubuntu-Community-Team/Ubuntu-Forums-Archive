---
title: "Sound through speakers but not headphones (9.04)"
date: 2009-10-06
forum: General Help
---

### Post by zdevil26 on 2009-10-06
I have a Compaq Presario CQ40 that I loaded with Ubuntu 9.04.

At first I didn't have any sound at all, so I scoured through this forum and found a fix that worked for most people. I updated ALSA and added these lines to /etc/modprobe.d/alsa-base.conf:

```
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
```

and this line to /etc/modprobe.d/options.conf:

```
 options snd-hda-intel model=dell-m4-2 
```

When I restarted everything worked fine. I had sound through the speakers, and it muted when I plugged headphones into the front jack. Sound would come through the headphones as well.

The next time I restarted, everything worked fine except the speakers would still play after I plugged headphones in. Sound will still come out of the internal speakers, but not headphones Any fixes for this? Here's my soundcard.

```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel 
```

---

### Post by Giblet5 on 2009-10-06
Right-click the speaker icon. Open the Volume Control. Click the Edit menu and select Preferences...

Under the Switches tab, is there a toggle for "Detect headphones" or "Mute Output When Headphones In Use" or something similar?

Enable that switch and click OK.

Now, on the Volume Control dialog, select the Switches tab. Put a checkmark next to that option and verify that it works as expected.


There is no standard for sound cards, their mixers, or their features. Every manufacturer provides different features and do so in completely different ways.

Those manufacturers don't provide software for Linux, so the Linux community tries to work around the manufacturers. It's not perfect but it usually works OK.

---

### Post by zdevil26 on 2009-10-06
There were no switches for "Mute headphones".
There was one for IEC958 and IEC958 Default PCM.
I checked both of those and then checked them off in the switches tab but no change with the headphones.

---

### Post by zdevil26 on 2009-10-10
Bump. Anything here? This seems like an odd case.

---

### Post by nikhilbhardwaj on 2009-10-10
try 
alsamixer
here there'll be an option for headphones

---

