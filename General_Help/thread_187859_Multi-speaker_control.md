---
title: "Multi-speaker control?"
date: 2006-06-03
forum: General Help
---

### Post by Curlydave on 2006-06-03
I have a 7.1 soundcard. How can I get sound to play from more than 2 of the channels? I can't find an option in the sound controls. Thanks!

---

### Post by Sutekh on 2006-06-03
What sort of sound card do you have?  Not the SB 7.1?

Have you opened up the alsamixer and unmuted all channels?
```
alsamixer
```

Is is properly identified by Ubuntu?
```
lspci | grep audio
```
Are the neccessary sound modules loaded?
```
lsmod | grep snd
```

Also it may help to look up your card on the [ALSA Soundcard Matrix.](http://www.alsa-project.org/alsa-doc/)

---

