---
title: "unmuting my volume"
date: 2009-11-01
forum: General Help
---

### Post by Monotoko on 2009-11-01
Hiya guys, i need something to unmute my volume at a certain time tomorow (as an alarm)

this command:

```
amixer set Master 60%
```

works, but only if the volume is unmuted....is there anyway i could make this command unmute my volume?

---

### Post by peculiar penguin on 2009-11-01
```
amixer set Master unmute
```?

---

### Post by Monotoko on 2009-11-01
one of the first things i tried, it doesnt work

```
  monotoko@Katie-II:~$ amixer set Master unmute
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [on]
monotoko@Katie-II:~$ amixer -c 0 set Master 65%
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 42 [66%] [-22.00dB] [on]
```

It says its on and working, but its still set muted on my taskbar and doesnt play anything...

---

### Post by peculiar penguin on 2009-11-01
Weird, works fine for me :confused:

---

