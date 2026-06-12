---
title: "Quake1 x11 sound problem"
date: 2006-03-17
forum: General Help
---

### Post by DanielSmith604 on 2006-03-17
I have proquake setup with the id1/pakfiles \\:D/ 

/usr/local/games/quake/pq3.5-quake.x11

My sound does not work tho and I was wondering if anyone else knows how I can enable it. (Dan <-- linux newb)

Here's what I get in startup if this helps:

[INDENT]Added packfile ./id1/pak0.pak (339 files)
Added packfile ./id1/pak1.pak (85 files)
PackFile: ./id1/pak1.pak : gfx/pop.lmp
Playing registered version.
PackFile: ./id1/pak0.pak : gfx.wad
Console initialized.
Could not initialize security module
UDP Initialized
Exe: 08:04:55 Nov 12 2005
 8.0 megabyte heap
PackFile: ./id1/pak0.pak : gfx/palette.lmp
PackFile: ./id1/pak0.pak : gfx/colormap.lmp
1312k surface cache
VID: shared memory id=5210113, addr=0xb7374000
VID: shared memory id=5242882, addr=0xb7248000

Sound Initialization
[COLOR="Red"]PackFile: ./id1/pak0.pak : gfx/conback.lmp
/dev/dsp: Input/output error
Could not mmap /dev/dsp
S_Startup: SNDDMA_Init failed.[/COLOR]
Sound sampling rate: 11025
CDAudio_Init: open of "/dev/cdrom" failed (123)
========Quake Initialized=========
Linux Quake -- Version 1.300
PackFile: ./id1/pak0.pak : quake.rc
execing quake.rc
PackFile: ./id1/pak0.pak : default.cfg
execing default.cfg
FindFile: ./id1/config.cfg
execing config.cfg
FindFile: can't find autoexec.cfg
couldn't exec autoexec.cfg [/INDENT]

---

### Post by DanielSmith604 on 2006-03-20
Actually the problem may be with my sound setup in general.

I havn't tampered with the sound since I installed ubuntu so it's default. In what ways can I change it?

---

