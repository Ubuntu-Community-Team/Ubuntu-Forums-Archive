---
title: "Aplay and mplayer sounds go out of sync"
date: 2009-08-28
forum: General Help
---

### Post by markp1989 on 2009-08-28
```
    aplay -q  -f dat /dev/video24 &
    DISPLAY=:0.1 mplayer -rawvideo format=hm12:h=480:w=720:fps=29.97 -nocache -demuxer 26 /dev/video32 -framedrop -vo xv -monitoraspect 16:10 -aspect 16:9 -fs &

```

im using this script to play sky tv from my haupage win tv 150

when i first run it, sound and video line up, but after a hour or so viewing , the sound tharts to be behind the video, after leaving it on all night, the sound was about 10 sec behind the video.

I had this working fine, then i tried to set up pulse audio, but pulse audio wouldnt work properly, so i went back to alsa, after that aplay wouldnt play sound, which took a while to fix, cannot remember how i got it working again, so i think this something to do with pulse, even thou its not installed any more.

any ideas?

Thanks Markp1989

---

