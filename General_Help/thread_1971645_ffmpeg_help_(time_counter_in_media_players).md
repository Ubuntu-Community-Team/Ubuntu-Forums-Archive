---
title: "ffmpeg help (time counter in media players)"
date: 2012-05-02
forum: General Help
---

### Post by Primefalcon on 2012-05-02
After converting and joining video's.....

I am having an issue with the time elapsed in media players showing an incorrect time on a joined/converted video/audio..... how do I fix this?

---

### Post by FakeOutdoorsman on 2012-05-03
Inadequate information supplied to provide a useful answer. Show your ffmpeg command(s) and the complete console output that you used to join the videos. What media players did you use? What Ubuntu version are you using?

---

### Post by Primefalcon on 2012-05-03
well it was several 15 secnd climbs taken using a photo camera (can take 15 second clips in mpeg format)

so I line them up and used cat to join them

```
cat vid1.mpeg vid2.mpeg vid3.mpeg vid4.mpeg > completevid.mpeg
```

then I used ffmpeg to convert over to mp4 format via...

```
ffmpeg -i completevid.mpeg -sameq completevid.mp4
```

and what has happened is that the whole video will play in either totem or vlc but it only counts up to 15 seconds (length of first clip), after that it keeps playing but the counter does not work...

ubuntu is version 12.04, was consodering on yanking ffmpeg and install avconv since ffmpeg has been kind of discontinued but (reason I have not is that avconv/libav does not appear to be in the repo's so would require compiling from souce which can take a bit on this system)...... this issue is one I have not had before (yeah I've done this sorta thing a lot)....

---

