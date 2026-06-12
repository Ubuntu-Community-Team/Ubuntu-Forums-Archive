---
title: "Volume Slider Commands"
date: 2010-02-21
forum: General Help
---

### Post by cd-r80 on 2010-02-21
Hi! I compiled & installed xfce4-generic-slider for my panel.
[http://goodies.xfce.org/projects/panel-plugins/xfce4-generic-slider](http://goodies.xfce.org/projects/panel-plugins/xfce4-generic-slider).

Commands are here:
Adjust this command: amixer set PCM %v
Denominator for adjusting: 31
Sychronize with this command: amixer get PCM | grep -Eom1 ‘[0-9]+%’ | sed -e ‘s/%//’
Denominator for sychronizing: 100

But my volume just slides back? What commands to control master? How to remove other volume control. I just removed it from panel, but now top says: "defunct xfce4-mix".

---

### Post by Brandon Williams on 2010-02-21
I have not used this plugin, but I do use amixer for the same purpose. It's possible that the denominator values you've chosen are not correct for your mixer. The 100 for synchronizing looks like it should be OK, since the output from the 'amixer get' command line is a percent of the total. The 31 could be a problem though. Run 'amixer get PCM' on the command line to figure out what that value should be. On the machine I'm working on now, I see this:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
```
The important line is the one labeled "Limits". Your denominator value should be the high number in the range. If your denominator is too high or too low, you will probably get strange behavior.

---

### Post by cd-r80 on 2010-03-02
I have tried:

amixer  set Master %v
amixer get Master | grep -Eom1 ‘[0-9]+%’ | sed -e ‘s/%//’

Denominator for adjusting: 64
Denominator for sychronizing: 100
Denominator for label: 100

When:
amixer get Master
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 18 [28%] [-46.00dB] [on]
  Front Right: Playback 18 [28%] [-46.00dB] [on]

I can change volume but the slider slides away? When I change volume to 80% it stays there but the slider don't stay. I have label for slider empty? (screenshot attached)

---

