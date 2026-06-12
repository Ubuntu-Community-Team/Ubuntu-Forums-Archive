---
title: "Nexuiz sound problem"
date: 2011-04-18
forum: General Help
---

### Post by MulattoJones on 2011-04-18
Hi there,
New user to Ubuntu and so far loving it, minus a few snags. Running 10.10 by the way. when I run Nexuiz I get this error.

```
Trying to load library... "libz.so.1" - loaded.
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/data20080229.pk3 (3992 files)
Added packfile data/data20091001.pk3 (9053 files)
Trying to load library... "libcurl.so.4" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Loading OpenGL driver libGL.so.1
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
effectinfo.txt:777: skipping unknown command stretchfactor
effectinfo.txt:3192: skipping unknown command stretchfactor
effectinfo.txt:4247: skipping unknown command stretchfactor
effectinfo.txt:4434: skipping unknown command stretchfactor
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
Sound format: 48000Hz, 2 channels, 16 bits per sample
ioctl CDROMREADTOCHDR failed
CDAudio_Init: No CD in player.
Initial CD volume: 1
CD Audio Initialized
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
couldn't exec unit_repulsor.cfg
execing default25.cfg
execing physics25.cfg
execing balance25.cfg
execing config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Menu_Error: No such builtin #514 in menu; most likely cause: outdated engine build. Try updating!
QuakeC crash report for menu:
s27728: STORE_F     (=_allow_unacceptable_compiler_bugs), GLOBAL4
s27729: CALL1      GLOBAL70
s27730: IFNOT      GLOBAL1, s27732
s27731: DONE       
s27732: STORE_F     (=foo bar), GLOBAL4
s27733: CALL1      GLOBAL249
             : check_unacceptable_compiler_bugs : statement 5
             : m_init : statement 4
Falling back to normal menu
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:42012
Draw_CachePic: failed to load gfx/mainmenu

```

I already removed Pulseaudio, any suggestions ?

Thanks in advance :D

---

