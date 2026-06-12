---
title: "padsp + dosemu in karmic"
date: 2009-11-28
forum: General Help
---

### Post by kjkrum on 2009-11-28
The SB emulation in dosemu was designed to work with OSS, so it attempts to open /dev/dsp directly. I've tried running it with -s, wrapping it with padsp, and both at the same time, but it still cannot access the sound card, as shown in the log below.  Then I tried editing /usr/bin/dosemu so that the command it executes is "$SUDO $PADSP $COMMAND ..." or "$PADSP $SUDO $COMMAND ...", to no effect.  lsof /dev/dsp reports nothing.

```
kevin@aphrodite:~/.dosemu$ padsp xdosemu -D +S
kevin@aphrodite:~/.dosemu$ cat boot.log | grep SB
SB: SB Initialisation
SB: Initialisation - Base 0x220, IRQ 5, DMA 1, HDMA 5
SB: FM Initialisation
SB:[Linux] FM Driver Initialisation Called
SB: Resetting SB
SB: Disabling Speaker
SB: Speaker already disabled
SB:[Linux] SB Driver Initialisation Called
SB: /dev/dsp open failed, Device or resource busy
SB:[Linux] No sounddevice for SoundBlaster emulation found.
SB: Resetting FM
SB:[Linux] FM Driver Reset Called
kevin@aphrodite:~/.dosemu$
```

dosbox works, but the sound is choppy and it takes over the mouse until it's closed.  I'd really like to get sound working in dosemu.

Edit: Using LD_PRELOAD on the command line instead of the padsp script doesn't work, but it changes the error message:

```
LD_PRELOAD=/usr/lib/libpulsedsp.so dosemu -D +S
...
SB: /dev/dsp open failed, Connection refused
```

But if I combine this with sudo, the error goes back to "Device or resource busy".

Edit2: Also tried unloading the OSS pcm, midi, and mixer kernel modules.  /dev/dsp ceases to exist and, unsurprisingly, dosemu's boot.log says file not found.  /dev/audio does not work; it behaves like /dev/dsp.  I feel like I might be onto something by attempting to use /dev/snd/pcmC0D0p or similar.  boot.log then says "SoundBlaster 2.0 can be emulated."  But sound doesn't actually work, and the log is littered with messages about driver resets and "Inappropriate ioctl for device".  This is true with or without padsp, with or without sudo.

After sleeping on it, I installed alsa-oss, changed dosemu back to using /dev/dsp, and double-wrapped it with padsp and aoss:

```
kevin@aphrodite:~$ LD_PRELOAD="libaoss.so libpulsedsp.so" dosemu -D +S
```

IT WORKS!  (Kind of.)  MIDI does not work, and pcm output longer than a couple seconds per clip gets cut off.

Edit3: I noticed that the message in boot.log changed from "SoundBlaster 2.0 can be emulated." to "SoundBlaster 16 can be emulated."  I changed my DOS app's sound settings to "SoundBlaster Pro (later)" and pcm now works almost perfectly; there's just a little pop and hiss audible whenever sound is played.  Still no MIDI, though...

---

