---
title: "movie to iso?"
date: 2010-11-17
forum: General Help
---

### Post by LuniTux on 2010-11-17
Hello,

I am trying to copy my dvds from cd to iso (or any other format) so that I can watch them on my netbook (Toshiba nb205). I have both windows XP and Ubuntu 9.10 on the netbook. It does not matter what the file format is as long as I can play it. I have tried multiple programs with no success. 

k3b - says movie is encrypted
acidrip - crashed
dvd::rip - cant figure out
k9copy - crashed
thoggen - crashed

Are there any other alternatives?


-----------
I just noticed that brasero can burn to iso

i found the file I was missing (libdvdcss.so.2) here

[http://ubuntuforums.org/showthread.php?t=1499045]("http://ubuntuforums.org/showthread.php?t=1499045")

---

### Post by northern lights on 2010-11-17
in the respective folder

```
cat FILL_ME_IN_00*.VOB > all.VOB
```

```
ffmpeg -y -i "all.VOB" -vcodec libx264 -vpre slow -b 1000k -bf 3 -b_strategy 1 -coder 1 -qmin 10 -qmax 51 -sc_threshold 40 -flags +loop -cmp +chroma -me_range 16 -me_method hex -subq 5 -i_qfactor 0.71 -qcomp 0.6 -qdiff 4 -directpred 1 -flags2 +fastpskip -dts_delta_threshold 1  -threads 0 -acodec libfaac -ab 256k -ar 44100 -async 44100 -ac 2 -deinterlace "FILL_ME_IN.mp4"
```

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

[http://linux.die.net/man/1/ffmpeg]("http://linux.die.net/man/1/ffmpeg")

---

### Post by asmoore82 on 2010-11-17
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

```
apt-cache show dvdbackup
```

[http://www.google.com/search?q=handbrake](http://www.google.com/search?q=handbrake)

---

### Post by LuniTux on 2010-11-18
brasero seems to give me what I want. Thanks for the help though :)

---

