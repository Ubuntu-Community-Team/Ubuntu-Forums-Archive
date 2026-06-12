---
title: "Audacious 3.1 : No decoder found for file [compiled]"
date: 2011-11-22
forum: General Help
---

### Post by elliotn on 2011-11-22
so o compiled audacious 3.1 from source as there is no 3.1 for 11.04, all went fine until o tried to play a mp3/wav/wma etc but I got 

 Audacious : No decoder
found for file ///.....mp3/wav/wma

what did I do wrong, I also compiled the plugins

---

### Post by elliotn on 2011-11-23
any suggestions

---

### Post by elliotn on 2011-11-24
any solution

---

### Post by elliotn on 2011-11-25
I have searched everywere

---

### Post by mc4man on 2011-11-25
Because of a bug I have on aud in 11.10 (no ffaudio), took a look tonight to see if fixing the configure/configure.ac would allow 2.4 in 11.10. It wouldn't as afar as ffmpeg so went ahead & built the current stable 3.1 & plugins.
Works fine here for all supported audio inc. wma2, wma3(pro

First thing - **before building audacious** did you remove all the audacious  packages you may have had installed
- EX.
> Commit Log for Thu Nov 24 17:51:05 2011

Completely removed the following packages:
audacious
audacious-plugins
libaudclient2
libaudcore1
And just prior to that 


> 
Commit Log for Thu Nov 24 17:44:51 2011
Completely removed the following packages:
libmcs-dev
libmowgli-dev

Removed the following packages:
audacious-dev

---

### Post by andrew.46 on 2011-11-25
Perhaps unhelpfully I have just finished compiling 3.1 on my 'other' distro and all went well. Can you post what your plugins compilation showed after the initial ./configure? My own is:

```

  Output Plugins
  --------------
  Open Sound System (oss4):               no
  Advanced Linux Sound Arch. (alsa):      yes
  PulseAudio (pulse):                     no
  RoarAudio (roaraudio):                  no
  Jack Audio Connection Kit (jack):       no
  Mac OS X sound support (CoreAudio):     no
  Simple DirectMedia Layer (sdlout):      yes
  FileWriter:                             yes
    -> FileWriter MP3 output part:        yes
    -> FileWriter Vorbis output part:     yes
    -> FileWriter FLAC output part:       yes
  Null Audio output (null):               yes
  Windows waveOut (experimental):         no
  OpenAL (experimental):                  no
  Open Sound System v3 (deprecated):      no

  Input Plugins
  -------------
  MPEG-1 Layer I/II/III (mpg123):         yes
  MPEG-2/4 AAC (aac):                     no
  FFaudio (ffaudio):                      yes
  Module decoder (modplug):               no
  MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                yes
  CD Digital Audio (cdaudio_ng):          yes
  sndfile extensions:                     yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flacng):     yes
  Commodore 64 audio (SID):               no 
    -> libSIDPlay1 support:               no
    -> libSIDPlay2 support:               no
    -> distortion patched libSIDPlay2:    
  Game music (spc, nsf & gbs):            yes
  PlayStation (psf/psf2) audio:           yes
  Nintendo 64 audio (usf) (experimental): no
  Nintendo DS audio (xsf):                yes
  AdLib synthesizer (adplug):             no
  WavPack 4.31+ (wavpack):                yes
  Metronom:                               yes

  General
  -------
  Alarm:                                  yes
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          yes
    -> X Composite support:               yes
  libnotify OSD:                          yes
  Global Hotkey Plugin:                   yes
  Gnome Shortcuts Plugin:                 yes
  AudioScrobbler Client:                  yes
  Upload to MTP device:                   yes
  MacOS Dock Album Art plugin:            no
  LyricWiki viewer:                       yes
  Album Art widget:                       yes

  Effect
  ------
  Channel Mixer:                          yes
  Crystalizer:                            yes
  Dynamic Range Compressor:               yes
  Echo/Surround:                          yes
  Extra Stereo:                           yes
  LADSPA Host:                            yes
  SndStretch:                             yes
  Voice Removal:                          yes
  Bauer stereophonic-to-binaural (bs2b):  no
  Sample Rate Converter (resample):       yes

  Visualization
  -------------
  Blur Scope:                             yes
  Cairo Spectrum Analyzer:                yes

  Transport
  ---------
  neon-based http/https:                  yes
  libmms-based mms:                       no
  GIO transport (experimental):           no
  SMB transport (experimental):           no

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes
  CUE playlist format (cue):              no

  Interfaces
  ----------
  GTK (gtkui):                            yes
  Winamp Classic (skins):                 yes

```

---

### Post by elliotn on 2011-11-25
> **andrew.46 said:**
> Perhaps unhelpfully I have just finished compiling 3.1 on my 'other' distro and all went well. Can you post what your plugins compilation showed after the initial ./configure? My own is:

```

  Output Plugins
  --------------
  Open Sound System (oss4):               no
  Advanced Linux Sound Arch. (alsa):      yes
  PulseAudio (pulse):                     no
  RoarAudio (roaraudio):                  no
  Jack Audio Connection Kit (jack):       no
  Mac OS X sound support (CoreAudio):     no
  Simple DirectMedia Layer (sdlout):      yes
  FileWriter:                             yes
    -> FileWriter MP3 output part:        yes
    -> FileWriter Vorbis output part:     yes
    -> FileWriter FLAC output part:       yes
  Null Audio output (null):               yes
  Windows waveOut (experimental):         no
  OpenAL (experimental):                  no
  Open Sound System v3 (deprecated):      no

  Input Plugins
  -------------
  MPEG-1 Layer I/II/III (mpg123):         yes
  MPEG-2/4 AAC (aac):                     no
  FFaudio (ffaudio):                      yes
  Module decoder (modplug):               no
  MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                yes
  CD Digital Audio (cdaudio_ng):          yes
  sndfile extensions:                     yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flacng):     yes
  Commodore 64 audio (SID):               no 
    -> libSIDPlay1 support:               no
    -> libSIDPlay2 support:               no
    -> distortion patched libSIDPlay2:    
  Game music (spc, nsf & gbs):            yes
  PlayStation (psf/psf2) audio:           yes
  Nintendo 64 audio (usf) (experimental): no
  Nintendo DS audio (xsf):                yes
  AdLib synthesizer (adplug):             no
  WavPack 4.31+ (wavpack):                yes
  Metronom:                               yes

  General
  -------
  Alarm:                                  yes
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          yes
    -> X Composite support:               yes
  libnotify OSD:                          yes
  Global Hotkey Plugin:                   yes
  Gnome Shortcuts Plugin:                 yes
  AudioScrobbler Client:                  yes
  Upload to MTP device:                   yes
  MacOS Dock Album Art plugin:            no
  LyricWiki viewer:                       yes
  Album Art widget:                       yes

  Effect
  ------
  Channel Mixer:                          yes
  Crystalizer:                            yes
  Dynamic Range Compressor:               yes
  Echo/Surround:                          yes
  Extra Stereo:                           yes
  LADSPA Host:                            yes
  SndStretch:                             yes
  Voice Removal:                          yes
  Bauer stereophonic-to-binaural (bs2b):  no
  Sample Rate Converter (resample):       yes

  Visualization
  -------------
  Blur Scope:                             yes
  Cairo Spectrum Analyzer:                yes

  Transport
  ---------
  neon-based http/https:                  yes
  libmms-based mms:                       no
  GIO transport (experimental):           no
  SMB transport (experimental):           no

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes
  CUE playlist format (cue):              no

  Interfaces
  ----------
  GTK (gtkui):                            yes
  Winamp Classic (skins):                 yes

```

ok I will post the when i return from work

---

### Post by markb69 on 2012-09-30
I am not certain why this works but it fixed my "no decoder found" error message:

1) click on Preferences
2) then click on Plugins
3) then click on General
4) enable Song Change plugin

---

