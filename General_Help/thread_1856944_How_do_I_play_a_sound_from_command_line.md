---
title: "How do I play a sound from command line?"
date: 2011-10-09
forum: General Help
---

### Post by cha0s619 on 2011-10-09
Hi,

I am making a script to count down a a set number of seconds and I want it to play a notification sound when it's done, maybe a door bell or something. Is this possible? I don't want it to open Banshee or any big program like that. Something light just so that I know that the script is done. Which command do I use?

Thanks

---

### Post by stinkeye on 2011-10-09
try
```
aplay -q /path/to/sound
```
I don't understand audio very well and the command won't play all my sound
files but the attached ding sound plays.

---

### Post by cha0s619 on 2011-10-09
It works. Thanks! :)

---

### Post by CaptainMark on 2011-10-09
aplay is good, light and simple, but i think it only plays .wav files or similar, use soundconverter from the software centre to convert other sounds you want to use to .wav

---

