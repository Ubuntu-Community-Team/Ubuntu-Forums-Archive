---
title: "No DVD/CD in ubuntu 10.04??"
date: 2010-07-04
forum: General Help
---

### Post by steve509 on 2010-07-04
Dear friends, I'm running 10.04 along with dual boot 9.10. I've tried playing music in 10.04 with Rhythmbox and nothing happens, I can't even open up the dvd player to show the files on it. I also tried playing a dvd using mplayer and the same thing happens. When i'm in 9.10, I can play music cd's but not dvd movies. Any suggestions???? Please help!!! Thanks in advance
steve509

---

### Post by Leppie on 2010-07-04
you may want to have a look at the medibuntu documentation: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by steve509 on 2010-07-04
Leppie, thanks for the reply. I have installed that many times already and still it never shows up in the SPM. I've installed the w64codecs, yes i have a 64 bit system, I've tried may other things i've found on google to get it going and still nothing. I am still new to ubuntu (about 3 months now) and am learning slowly but surely but I still cannot get this darn (want to use much stronger language) thing going but just can't. As much as i LOVE ubuntu 9.10 and now 10.04, i'm getting very frustrated....PLEASE, PLEASE, SOMEONE, EVERYONE...HELP!!!! :)
Thanks

steve509

---

### Post by Leppie on 2010-07-04
now, about your dvd problem do you have the decss2 package installed on both installs?
```
sudo apt-get install libdvdcss2
```

and the music, what kind of files are those? (mp3, wav, wma, etc)

---

