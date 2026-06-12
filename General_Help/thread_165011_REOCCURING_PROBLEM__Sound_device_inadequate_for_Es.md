---
title: "REOCCURING PROBLEM : Sound device inadequate for Esound. Fatal. --- PLEASE HELP!"
date: 2006-04-23
forum: General Help
---

### Post by lopzided on 2006-04-23
this problem is driving me nuts...i can't find the answer anywhere!

a lot of times, when certain commands are run from console, i get this:

```
juztin@ubuntujuztin:~$ sudo gedit /etc/default/prelink
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.

```

i don't know if this is related or not, but the sounds that usually play when ubuntu starts up (the bongos at login and the atmospheric sound during the splash screen) no longer work.

i have been searching for days and can't find the answer to this, please help!

---

### Post by lopzided on 2006-04-23
bump!  please help!

---

### Post by lopzided on 2006-04-25
<sigh>...bump!
am i really the only person having this problem? :(

---

### Post by lopzided on 2006-04-25
bump
please!

---

### Post by demetrisk on 2006-09-09
Anyone knows how to solve this? I'm on 6.06

Thanks!

---

### Post by ClockworkMonk on 2006-10-21
Seconded. I've been trying to fix this for ages, and getting nowhere. There's no apparent connection between the commands I'm running and the sound device, and sound works fine in apps that need it.

Very odd. Very frustrating.

CM

---

### Post by demetrisk on 2006-10-22
**ClockworkMonk**, it seems, in my case, this had to do with another issue, the configuration of my two sound devices. Once I solved this, the terminal issue disappeared.

See here: [http://www.hydrogenaudio.org/forums/index.php?showtopic=48385](http://www.hydrogenaudio.org/forums/index.php?showtopic=48385)

---

