---
title: "Tovid sound error. Help please?"
date: 2006-02-14
forum: General Help
---

### Post by RaiSuli on 2006-02-14
Hi,

when trying to convert avi into vcd, tovid gives me the following error:

[tovid]: Creating WAV of audio stream with the following command:
[tovid]: nice -n 0 mplayer -quiet -vc null -vo null -ao pcm:waveheader:file=audiodump.wav "/externhd/mars1x01.avi"
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Foster (Family: 8, Stepping: 7)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.

Option srate needs a parameter at line 143
[tovid]: Encode stopped, killing all sub processes
[tovid]: tovid encountered an error during encoding:
[tovid]:     Couldn't create file: "audiodump.wav"

According to the Tovid homepage, all necessary dependencies have been installed, the programme starts without any warnings or errors. I've tried converting three different avis now with the same result.

Any ideas?

---

### Post by RaiSuli on 2006-02-15
No one? 
I really need this for encoding mpegs because my stand alone player can't play avi files. Or maybe there is another software (CLI or GUI) that can do the trick. Tried Avidemux, but just got a ton of error messages when running it.

---

