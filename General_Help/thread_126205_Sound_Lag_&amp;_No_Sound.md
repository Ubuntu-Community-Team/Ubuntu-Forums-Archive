---
title: "Sound Lag &amp; No Sound"
date: 2006-02-05
forum: General Help
---

### Post by Mau on 2006-02-05
I think I'm finally come to my end of 101 questions.  But, here's one more.  \\:D/ 

I think there might be something funky going on with my sound.  I have noticed that whenever some alert box comes up, or press back space in Konsole with a blank command, I hear the alert tone slightly late.  I guess light is suppose to be faster than sound, but not that much faster!

Secondly, I'm getting odd behavior with sound when using a game.  Whenever I launch Tux Racer, for example, I get sound about 50% of the time.  I recently installed some other game (Wolfenstein?) and there no sound, even though it seemed like there should have been.  It's not a big deal; I don't play games that much, but I am curious to see as to why sound will not work.

Any ideas on what could be going on?  When I go to System Settings > Sound > Test Sound, I get nothing for about a second, and then the tone plays.  When I press Test MIDI, I hear nothing.

KInfoCenter says that I'm using:
```

Sound Driver: 3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux carl 2.6.12-10-386 # 1 Mon Jan 16 17:18:08 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
SiS S17012 with CMI9739 at 0xe400, irq 18

Audio devices:
0: SiS S17012 (DUPLEX)

Synth devices: Not enabled in config

Midi devices: Not enabled in config

Timers:
7: system timer

Mixers:
0: C-Media Electronics CMI9739
```

I have a feeling it has to do with midi devices?

---

### Post by Mau on 2006-02-07
Any ideas?

---

### Post by moopere on 2006-02-07
[QUOTE=Mau]Any ideas?[/QUOTE]


Not many I'm afraid - the sound lag thing has bugged me in KDE for years.  I'm tempted to think its something to do with the ARTS daemon because you don't seem to suffer this sound lag using esd under gnome.

If it is ARTS then we'll have to wait until KDE4 and the replacement of ARTS with something else to get any joy I'm afraid.

Regards,
Craig

---

