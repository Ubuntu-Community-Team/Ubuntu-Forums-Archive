---
title: "sound output crippled by firefox (alsa issues?)"
date: 2010-01-25
forum: General Help
---

### Post by suzenon on 2010-01-25
I've had problems with my sound that i mentioned in this topic: [http://ubuntuforums.org/showthread.php?t=1386194](http://ubuntuforums.org/showthread.php?t=1386194) but noone answered so i started trying things.

I've updated ALSA and managed to partially achieve what i wanted to, but other things gets messed even worse. I've get rid of choppy sounds problems and i can get sound from few applications UNLESS firefox isn't one of them.

The problem is. If i start firefox first, and open a page that is using sound for example youtube and start a vid. Sound from all other applications is somehow blocked untill i'll turn off firefox. Or, when i start a music player, open firefox, pause player, start vid on youtube i have no sound from firefox.

What's weird is that i started quakelive (a web browser based game), started a movie in vlc, and went to system > preferences > Sound / Programs using output atm tab. And there was no apps at all, and both, firefox and vlc were playing sound. (screenshot attached to show this)

Can anyone help please? How can i make firefox not to 'take' whole sound output?

btw.
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     U&#379;YTKOWNIK  PID DOST&#280;P POLECENIE
/dev/snd/controlC0:  btz        1996 F.... pulseaudio
/dev/snd/pcmC0D0p:   btz        1996 F...m pulseaudio
```

---

### Post by andersja on 2010-01-25
It looks like you are using PulseAudio, and your problems may be associated with that? 

Check out padevchooser and/or "earcandy"

sudo aptitude install padevchooser
sudo aptitude install earcandy

---

### Post by suzenon on 2010-01-26
Well... my sound is so much #$^&#$^@ in ubuntu. PA and ALSA are just not cooperating.

I've managed to make things work as it should be, i was reinstalling alsa, pulse and ff untill it started to work properly. And it was fine for a day or two.

Now after few reboots all problems from beginning are back. Choppy sound in vlc, in addition when i start ubuntu everything is somehow muted untill i alsa force-reload. So it's even worse than it was before. Dunno what happend but my alsa version suddenly switched from 1.0.22.1 to 1.0.21. That's a real mistery, why just like that, my newest alsa installation disappeared.

I slowly having enought dealing with these damn problems. I don't know what this earcandy is, but maybe i'll try it. Atm i don't know if it would be good idea to add new software when all previous is so much messed up.

---

