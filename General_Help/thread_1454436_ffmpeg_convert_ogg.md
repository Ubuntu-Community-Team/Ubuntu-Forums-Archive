---
title: "ffmpeg convert ogg"
date: 2010-04-14
forum: General Help
---

### Post by filomena on 2010-04-14
What are the proper ffmpeg instructions for converting .ogg files to .mp3?  I have followed several formulas, but each time I get an error message.
ffmpeg -i file.ogg file.mp3 yields no codec available
ffmpeg -i file.ogg -acodec copy file.mp3 yields no data in file
ffmpeg -i file.ogg copy file.mp3 yields no stream

---

### Post by nothingspecial on 2010-04-14
```


sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get remove --purge ffmpeg && sudo apt-get install ffmpeg
```

Then try again

---

### Post by andrew.46 on 2010-04-14
Hi filomena,

> **filomena said:**
> What are the proper ffmpeg instructions for converting .ogg files to .mp3?  

You may be coming to grief because your copy of FFmpeg is not setup for mp3 transcoding. Try following the instructions here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If you set this up successfully could you then run one of your ogg files in this fashion:

```
ffmpeg -i my_file.ogg
```

where you will need to substitute *my_file.ogg* for the actual name of your file. If you then post the *full* terminal output produced by this command in this thread it will be a simple matter to suggest the appropriate commandline to you.

All the best,

Andrew

---

### Post by filomena on 2010-04-15
> **andrew.46 said:**
> Hi filomena,



You may be coming to grief because your copy of FFmpeg is not setup for mp3 transcoding. Try following the instructions here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If you set this up successfully could you then run one of your ogg files in this fashion:

```
ffmpeg -i my_file.ogg
```

where you will need to substitute *my_file.ogg* for the actual name of your file. If you then post the *full* terminal output produced by this command in this thread it will be a simple matter to suggest the appropriate commandline to you.

All the best,

Andrew
Thank you for the suggestions.  I have removed and replaced ffmpeg and then did ffmpeg -i <filename.ogg>  Below is the output:

  	 	 	 	 	 	  vincenzo@vincenzo-desktop:~/Music/Eileen Farrell/Sings Rodgers & Hart$ ffmpeg -i "1 - I Could Write A Book.ogg" 
 FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al. 
   configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static 
   libavutil     49.15. 0 / 49.15. 0 
   libavcodec    52.20. 0 / 52.20. 0 
   libavformat   52.31. 0 / 52.31. 0 
   libavdevice   52. 1. 0 / 52. 1. 0 
   libavfilter    0. 4. 0 /  0. 4. 0 
   libswscale     0. 7. 1 /  0. 7. 1 
   libpostproc   51. 2. 0 / 51. 2. 0 
   built on Oct 13 2009 22:15:16, gcc: 4.4.1 
 Input #0, ogg, from '1 - I Could Write A Book.ogg': 
   Duration: 00:02:34.20, start: 0.000000, bitrate: 167 kb/s 
     Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 160 kb/s 
 At least one output file must be specified

---

### Post by nothingspecial on 2010-04-15
Try ```
ffmpeg -i 1\ -\ I\ Could\ Write\ A\ Book.ogg I_Could_Write_A_Book.mp3
```

You have to tell ffmpeg what you want at the end.

The quotes, \s or _s  are equally valid. 

Bash doesn`t like spaces.

I hope you understand that.

---

### Post by andrew.46 on 2010-04-15
Hi filomena,

You could try:

```
ffmpeg -i '1 - I Could Write A Book.ogg' -acodec libmp3lame -ab 165k '1 - I Could Write A Book.mp3'
```

which is roughly what nothingspecial has mentioned but with the addition of *-ab 165k* and also the addition of the encoder's name. If the bitrate is not entered you will receive the default of 64k for your output file so it is often a good idea to have a look at the bitrate of the *input file* and attempt to match it to the bitrate of the *output file*, or even decrease it.

As for spaces, in general spaces are a bad idea, as nothingspecial has mentioned, but can be shielded by escaping them with the \ character, or by use of the " character if you wish to allow variable expansion or simply in this case by use of the ' character as I have done :).

All the best,

Andrew

---

### Post by ron999 on 2010-04-15
...........

---

### Post by andrew.46 on 2010-04-15
Hi ron999,

> **ron999 said:**
> Are you sure that **-acodec libfaac** is correct?
Surely that's not an mp3 codec.

Ooops.... temporary brainsnap.... :(. I will edit this mistake out before anybody else sees it :).

Andrew

---

### Post by FakeOutdoorsman on 2010-04-15
> **andrew.46 said:**
> Hi filomena,

You could try:

```
ffmpeg -i '1 - I Could Write A Book.ogg' -acodec libmp3lame -ab 165k '1 - I Could Write A Book.mp3'
```

which is roughly what nothingspecial has mentioned but with the addition of *-ab 165k* and also the addition of the encoder's name. If the bitrate is not entered you will receive the default of 64k for your output file so it is often a good idea to have a look at the bitrate of the *input file* and attempt to match it to the bitrate of the *output file*, or even decrease it.

...

All the best,

Andrew

You can also try *-aq* instead of *-ab*:
```
ffmpeg -i '1 - I Could Write A Book.ogg' -acodec libmp3lame -aq 4 '1 - I Could Write A Book.mp3'
```
I believe this will create a variable bit rate audio (VBR) file, while *-b* will create a constant bit rate (uuhh...CB...R?, yeah, that's it, CBR.  I am so smrt.) file.

I haven't used *-aq* as much as I should be although I personally usually encode MP3 audio as VBR when I use *lame* by itself.  One thing to note is that the FFmpeg help (*ffmpeg -h*) says that *-aq* is codec specific, so you would have to consult each encoder to find an appropriate value (or read the FFmpeg source code).  I'm guessing *-aq 4* should be similar to *lame -V4*.  My limited tests show this to be ~true.  Don't know what value you should be using?  See: [LAME - Hydrogenaudio Knowledgebase](http://wiki.hydrogenaudio.org/index.php?title=LAME).

---

### Post by FakeOutdoorsman on 2010-04-15
Talking about *lame*, you could also use FFmpeg to decode the audio and pipe it to lame to do the encoding:
```
ffmpeg -i '1 - I Could Write A Book.ogg' -f wav - | lame -V4 - '1 - I Could Write A Book.mp3'
```
Pipes are useful. | for President.

---

### Post by filomena on 2010-04-16
Thank you all for helping solve this problem.  I took FakeOutdoorsman's advice and piped it to lame which worked quickly and easily.  Slowly but surely, I think I might actually learn how to use linux.

---

