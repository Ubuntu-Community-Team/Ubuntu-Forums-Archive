---
title: "wget still downloads while mencoder encoding?"
date: 2009-12-16
forum: General Help
---

### Post by mysoogal on 2009-12-16
```
wget -o - http://www.movie-list.net/classics/last_action_hero.mov | mencoder last_action_hero.mov -o last_action_hero.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame 
```

it seems mencoder is doing the encoding while wget still downloads data thus mencoder finished before wget could finish the download, and half video is encoded

is there some type of wait function to use here ? so when wget completes download then i can start mencoder ?

---

### Post by dcstar on 2009-12-16
> **mysoogal said:**
> ```
wget -o - http://www.movie-list.net/classics/last_action_hero.mov | mencoder last_action_hero.mov -o last_action_hero.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame 
```

it seems mencoder is doing the encoding while wget still downloads data thus mencoder finished before wget could finish the download, and half video is encoded

is there some type of wait function to use here ? so when wget completes download then i can start mencoder ?
Try:
```
wget -o - http://www.movie-list.net/classics/last_action_hero.mov && mencoder last_action_hero.mov -o last_action_hero.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame 
```

---

### Post by mysoogal on 2009-12-17
thanks for that, when i use it i dont get the output of wget -o 

it seems stuck until video is downloaded, then i get output of mencoder when it starts

so i can also add another ffmpeg link with && ?

---

### Post by mysoogal on 2009-12-17
> **mysoogal said:**
> thanks for that, when i use it i dont get the output of wget -o 

it seems stuck until video is downloaded, then i get output of mencoder when it starts

so i can also add another ffmpeg link with && ?



found the answer , to get the progress information i had to use > wget [http://etc](http://etc) instead > of wget -0 - http:// etc

hope that helps anybody else

---

