---
title: "Music &amp; multiple X sessions"
date: 2010-04-13
forum: General Help
---

### Post by ubeto on 2010-04-13
Hello all,

I use two x session, one for xbmc and the other for my desktop, that i can switch with CTRL+ALT+F7 or CTRL+ALT+F8.

I start music in xbmc xsession and then switch to my desktop.

When the track is finish the next track don't play, i must to come back to xbmc xession and automatically the next track is playing.

I would like to have music all time when i'm not in xbmc xsession but in desktop xsession.

Could you help me ?

Thanks !
__________________
XBMC 9.11 R26018 (COMPILED : DEC 24 2009) PPA:TEAM-XBMC
Ubuntu 9.10 x86_64 2.6.31-19-generic
ATI Radeon HD 4200 512MB (ATI Catalyst drivers 10.2)

---

### Post by nixclusive on 2010-04-13
```
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO SDL] using aalib audio driver.
[AO SDL] Unable to open audio: No available audio device
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

I get the above error in mplayer when it attempts to play the next track on the command line while another X session is open somewhere. However, invoking mplayer again does not pose any problems. I'd like help with this too, thanks.

---

### Post by ubeto on 2010-05-18
up

__________________
XBMC 9.11 R26018 (COMPILED : DEC 24 2009) PPA:TEAM-XBMC
Ubuntu 9.10 x86_64 2.6.31-19-generic
ATI Radeon HD 4200 512MB (FGLRX drivers 9.10)

---

