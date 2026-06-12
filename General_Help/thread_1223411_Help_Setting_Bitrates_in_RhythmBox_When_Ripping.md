---
title: "Help: Setting Bitrates in RhythmBox When Ripping"
date: 2009-07-26
forum: General Help
---

### Post by WolfyAU82 on 2009-07-26
When setting the bitrate and format using Rhythmbox the initial selection is quite limited, but when I try to edit that format to get a higher bitrate I find there's a line of parameters.

When I rip CD into MP3 format it only rips into 128kps...

How do edit the settings to rip records (CD) into MP3 @192kps using Rhythmbox?

---

### Post by CatKiller on 2009-07-26
Rhythmbox uses your GStreamer pipelines to rip music. So it will use the same settings as SoundJuicer and the like. To get 192 you could go to Edit &#8594; Preferences &#8594; Music &#8594; Preferred format &#8594; Edit... and change the pipeline to something like

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=192 ! id3v2mux
```

---

### Post by WolfyAU82 on 2009-08-03
thanks for that, it's working nicely :-D

---

### Post by MentatGhola on 2012-09-10
Whenever I have used sound juicer I couldn't set the bitrate directly i had to set quality=(some numeric value like .7 or 1), with each value corresponding to a bitrate with 1 corresponding to 320kbps or something dont remember.

Anyway in the settings I have preferred format set to ogg but there the edit option is grayed out.  Switched to flac and mp3, same deal.  Downloaded soundjuicer, checked it was set to ogg, no options for command input...

???

---

