---
title: "Ogg conversion"
date: 2006-03-26
forum: General Help
---

### Post by LinuxKid on 2006-03-26
so I was thinking what the best way to go through using ubuntu without having access to the internet much and without having it installed on the hard drive to save it

now I really like my media and any OS I use must have it, however I know the difficulties with ubuntu and I'm willing to let them go because of the OS itself (including the first distro to work with my interenet connection :) ) so I thought that maybe I should convert them into ogg so that I can use them on ubuntu easily

so does anyone have some suggestions of ogg converters (for both video and audio), preferably if they could be done on windows

thanks for you time

(for some reason; I always have to say my life story before I ask a question, I really should get rid of that habit ](*,) )

---

### Post by IYY on 2006-03-27
Getting Ubuntu to play MP3 files is really not a problem, just a matter of typing one or two lines into the terminal. Even though I support open formats and always rip my CD's to OGG, I wouldn't suggest converting your files. Whenever you convert from one lossy format to another, you lose some quality.

If you still have the original CD's, you should rip straight to OGG. Otherwise, keep the MP3 files.

---

### Post by DOtSlaSHuCantCME on 2006-03-27
try "Kwave" ,my ogg (convert from mp3)files be too big tho. Its in synaptic

---

### Post by bionnaki on 2006-03-27
sudo apt-get install soundconverter

I'm pretty sure you'll need to install all the w32 codecs etc before you can use it, however.

I recommend just keeping the mp3s as is and ripping to ogg/flac in the future.

---

### Post by akiro.yamamoto on 2006-03-27
Same here, converting to .ogg from .mp3 is really not a viable option. Keep the .mp3 file you already have. Just follow the Restricted Formats Guide to enable
.mp3 playback on your system and convert all future rips to .ogg.

BTW:
In case no one else has said it.....
Welcome to Ubuntu Linux ;)
Check My Sig for Documentation Links....

---

### Post by Jergar on 2006-03-27
Using the flac format, which is a lossless format, gives you the freedom to later convert in a format you wish without loosing quality. 
I'm used to rip all my CDs in flac and convert in ogg for daily use.

:wq Wolf

---

### Post by Lord Illidan on 2006-03-27
There is no need to convert them. I have some 5 gigs of mp3s on my ubuntu box. They work beautifully..

---

### Post by gpeck157 on 2006-03-27
> **LinuxKid]so I was thinking what the best way to go through using ubuntu without having access to the internet much and without having it installed on the hard drive to save it

now I really like my media and any OS I use must have it, however I know the difficulties with ubuntu and I'm willing to let them go because of the OS itself (including the first distro to work with my interenet connection :) ) so I thought that maybe I should convert them into ogg so that I can use them on ubuntu easily

so does anyone have some suggestions of ogg converters (for both video and audio), preferably if they could be done on windows

thanks for you time

(for some reason said:**
> (*,) )

Mp3's play just fine using Ubuntu. I have found Audacity and Sound Converter to be good choices for converting music files if need be. I have Audacity installed in both my Windows XP and in Ubuntu. Good luck...

Glen

---

### Post by LinuxKid on 2006-03-27
I didn't want to convert them in the first place, but I can't really install the mp3 formats (automatix doesn't work on dapper remember)

anyone got the terminal code, I'll guess I'll try that

---

### Post by gpeck157 on 2006-03-29
[QUOTE=LinuxKid]I didn't want to convert them in the first place, but I can't really install the mp3 formats (automatix doesn't work on dapper remember)

anyone got the terminal code, I'll guess I'll try that[/QUOTE]

I'm not using Dapper, but if Sound Converter is in the repositories, then it's

```
sudo apt-get install soundconverter
```

Good luck,

Glen

---

