---
title: "cdrdao and burning a .cue from a CLI environment"
date: 2011-09-25
forum: General Help
---

### Post by chinaCat86 on 2011-09-25
Being an early adopter of mp3 players (pre ipods), I haven't burned an Audio CD in well over a decade. My girlfriend still likes to use her cd player because she is limited to 8gbs.I want to surprise her with some cds. 

Naturally I want to give her quality. I have a lot of .flacs/.cue files laying around. This happens when you are a fan of bands with live recording policies. Anyhow, the .cue files point to .wav's which is expected for an audio cd to work(?). 

```
flac -d *.flac
```

takes care of this very simply. At this point I would like to utilze the .cue files. WHile I prefer a CLI solution, I am open to alternatives. 

```
cdrdao write *.cue
```

cdrdao looks to be the tool do this, but when I try to burn the .cue file on multiple machines with multiple settings It returns with the error `Pregap out of range`

With this I am at a loss, could it be the .cue? ** what does Pregap out of Range mean? **

here is the .cue I am trying:

> TITLE "1972.04.07 - Wembley Empire Pool - London, ENG (Disc 1)"
PERFORMER "Grateful Dead"
CATALOG 0081227978051
REM DATE "1972"
REM DISCNUMBER 1
REM TOTALDISCS 3
REM DISCID A40EE30C
REM REPLAYGAIN_ALBUM_GAIN -6.55 dB
REM REPLAYGAIN_ALBUM_PEAK 0.972443
FILE "01 Greatest Story Ever Told.wav" WAVE
  TRACK 01 AUDIO
    TITLE "Greatest Story Ever Told"
    ISRC USRH11001268
    REM REPLAYGAIN_TRACK_GAIN -5.81 dB
    REM REPLAYGAIN_TRACK_PEAK 0.970306
    INDEX 01 00:00:00
FILE "02 Sugaree.wav" WAVE
  TRACK 02 AUDIO
    TITLE "Sugaree"
    ISRC USRH11001269
    REM REPLAYGAIN_TRACK_GAIN -5.48 dB
    REM REPLAYGAIN_TRACK_PEAK 0.971985
    INDEX 01 00:00:00
FILE "03 Chinatown Shuffle.wav" WAVE
  TRACK 03 AUDIO
    TITLE "Chinatown Shuffle"
    ISRC USRH11001270
    REM REPLAYGAIN_TRACK_GAIN -7.05 dB
    REM REPLAYGAIN_TRACK_PEAK 0.971558
    INDEX 01 00:00:00
FILE "04 Me and My Uncle.wav" WAVE
  TRACK 04 AUDIO
    TITLE "Me and My Uncle"
    ISRC USRH11001271
    REM REPLAYGAIN_TRACK_GAIN -6.96 dB
    REM REPLAYGAIN_TRACK_PEAK 0.971039
    INDEX 01 00:00:00
FILE "05 China Cat Sunflower>.wav" WAVE
  TRACK 05 AUDIO
    TITLE "China Cat Sunflower>"
    ISRC USRH11001272
    REM REPLAYGAIN_TRACK_GAIN -6.39 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972290
    INDEX 01 00:00:00
FILE "06 I Know You Rider.wav" WAVE
  TRACK 06 AUDIO
    TITLE "I Know You Rider"
    ISRC USRH11001273
    REM REPLAYGAIN_TRACK_GAIN -6.85 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972351
    INDEX 01 00:00:00
FILE "07 Big Boss Man.wav" WAVE
  TRACK 07 AUDIO
    TITLE "Big Boss Man"
    ISRC USRH11001274
    REM REPLAYGAIN_TRACK_GAIN -7.49 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972351
    INDEX 01 00:00:00
  TRACK 08 AUDIO
    TITLE "Black Throated Wind"
    ISRC USRH11001275
    REM REPLAYGAIN_TRACK_GAIN -6.19 dB
    REM REPLAYGAIN_TRACK_PEAK 0.969666
    INDEX 00 04:38:63
FILE "08 Black Throated Wind.wav" WAVE
    INDEX 01 00:00:00
FILE "09 Loser.wav" WAVE
  TRACK 09 AUDIO
    TITLE "Loser"
    ISRC USRH11001276
    REM REPLAYGAIN_TRACK_GAIN -5.06 dB
    REM REPLAYGAIN_TRACK_PEAK 0.969025
    INDEX 01 00:00:00
FILE "10 Mr. Charlie.wav" WAVE
  TRACK 10 AUDIO
    TITLE "Mr. Charlie"
    ISRC USRH11001277
    REM REPLAYGAIN_TRACK_GAIN -6.24 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972321
    INDEX 01 00:00:00
FILE "11 Beat It On Down the Line.wav" WAVE
  TRACK 11 AUDIO
    TITLE "Beat It On Down the Line"
    ISRC USRH11001279
    REM REPLAYGAIN_TRACK_GAIN -7.93 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972351
    INDEX 01 00:00:00
FILE "12 Tennessee Jed.wav" WAVE
  TRACK 12 AUDIO
    TITLE "Tennessee Jed"
    ISRC USRH11001281
    REM REPLAYGAIN_TRACK_GAIN -6.51 dB
    REM REPLAYGAIN_TRACK_PEAK 0.972443
    INDEX 01 00:00:00

--

I have tried this with other .cue's and receive the same error.

---

### Post by chinaCat86 on 2011-09-26
Still no clue, I feel like it may be the .cue, but trying other .cues I come across the same error....

---

### Post by chinaCat86 on 2011-10-02
How upsetting. I am burrrning the discs through burrrn. Had to install wine for this (painless process) but upsetting none the less. Thought I'd update my progress in case anyone comes across this problem in the future....or if someone wishes to update this and offer a solution. 

I have tried installing patches available for cdrdao and installing from source the newer version.

k3b works well too, but for burning Audio CDs from Cue I need to use burrrn. Another Note is that this was largely to control gaps and CD-TEXT. Audacious will display cd text, many other players will not. However, you need to goto component > play cd for it to read the cd-text. I found just opening with Audacious did not work.

---

