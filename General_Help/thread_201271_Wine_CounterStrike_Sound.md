---
title: "Wine: CounterStrike Sound"
date: 2006-06-21
forum: General Help
---

### Post by Pooch on 2006-06-21
Hi,

I recently downloaded CounterStrike and tried running it with Wine. I had a few problems, but managed to fix them. The game runs fine except that CounterStrike has no audio. This might be a problem with CounterStrike, or it could be something wrong with Wine. Any ideas?

**Edit:** I got the audio to work, kind of. Everything seems to be lagging now, audio, video, input. Anything I can do in Winecfg to fix it?

---

### Post by ubu-for on 2006-06-26
[QUOTE=Pooch]I got the audio to work, kind of. Everything seems to be lagging now, audio, video, input. Anything I can do in Winecfg to fix it?[/QUOTE]

I have the same problem with CS Source.

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
The (slower) DirectSound HEL mode will be used instead.
```

Turn off the sound in Winecfg and the lagging is solved. But the game is without sound nearly unplayable. So ...

---

### Post by maka on 2006-06-26
[QUOTE=ubu-for]I have the same problem with CS Source.

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
The (slower) DirectSound HEL mode will be used instead.
```

Turn off the sound in Winecfg and the lagging is solved. But the game is without sound nearly unplayable. So ...[/QUOTE]


hmm ihave this problem too.. anyone know a solution?

---

### Post by der_joachim on 2006-06-27
When running Steam, try setting OSS as the sound driver instead of ALSA. [This page]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") has a lot of useful tips for configuring Wine with Steam.

---

### Post by ubu-for on 2006-06-27
[QUOTE=der_joachim]When running Steam, try setting OSS as the sound driver instead of ALSA. [This page]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") has a lot of useful tips for configuring Wine with Steam.[/QUOTE]

I've already tried every variety.

```

:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

```

:~$ WINEDEBUG=-all wine 'c:\Programme\Steam\Steam.exe' -fullscreen -width 1024 -height 768 -applaunch 240 -heapsize 512000
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.

```

OSS causes not such lagging as big as ALSA, but everytime I switch between the desktop and CSS, I get noise instead of sound.

---

