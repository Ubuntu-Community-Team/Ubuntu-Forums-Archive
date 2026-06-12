---
title: "Video to MP3 converters?"
date: 2012-07-02
forum: General Help
---

### Post by Beatsleigher on 2012-07-02
Hey guys!

I'm looking for a video to MP3 converter.
Does anyone have an idea, if something like this even exists for Ubuntu/Linux and if does, can someone please provide me with a link?

Thanks! Beatsleigher

---

### Post by ajgreeny on 2012-07-02
ffmpeg will do that easily.  If you want a GUI try winff.

---

### Post by bryncoles on 2012-07-02
Apparently, ffmpeg is being depreciated!  So instead, you can use avconv.  Open a terminal, firstly, cd to the directory you have your video file in. Then simply type:

```
avconv -i input.avi -ac 2 -ab 384k output.mp3
```

Lets break it down:

AVconv		this is the software doing the work. 

-i input.avi	the input file -- the file whose audio you want to take. Note that the extension need not be .avi. 

-ac2		number of audio channels (default is 1)

-ab 384k	the biterate to code at. 

output.mp3	the extracted audio file. Note it need not be an .mp3, if you don't want it to be.

---

### Post by FakeOutdoorsman on 2012-07-02
More specifically, Ubuntu switched to a fork of FFmpeg and the fork's version of "ffmpeg" is being depreciated (and has since been removed upstream).

ffmpeg from FFmpeg is alive and well.

---

### Post by bryncoles on 2012-07-02
> **FakeOutdoorsman said:**
> More specifically, Ubuntu switched to a fork of FFmpeg and the fork's version of "ffmpeg" is being depreciated (and has since been removed upstream).

ffmpeg from FFmpeg is alive and well.

Yay!  So it lives still?  My usage of ffmpeg to extract audio resulted in me being told by the terminal to use avconv instead.  The same switches I listed seem to work with ffmpeg though.  Should work with FFmpeg too I guess...

---

### Post by Beatsleigher on 2012-07-02
Cheers for the answers, guys! Much appreciated! Finally, I can rip the audio!

But, before I start and get confused, this isn't built in, is it? ^^

---

### Post by andrew.46 on 2012-07-03
> **bryncoles said:**
> Yay!  So it lives still? 

For FFmpeg have a look here:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Well worth following this guide...

---

### Post by bryncoles on 2012-07-03
> **Beatsleigher said:**
> Cheers for the answers, guys! Much appreciated! Finally, I can rip the audio!

But, before I start and get confused, this isn't built in, is it? ^^

On my system (Xubuntu 12.04) both ffmpeg and avconv are built in.  Should be the same on yours.   As you have seen from some of the above comments, when I try and use ffmpeg, I get told it won't be in future releases (but it will still be available -- yay!).  avconv seems to work fine though so there's no problem.  

Just open a terminal and type 
```
avconv
```

and if it says 

avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man avconv'

then you have it installed!

---

### Post by Beatsleigher on 2012-07-04
> **bryncoles said:**
> On my system (Xubuntu 12.04) both ffmpeg and avconv are built in.  Should be the same on yours.   As you have seen from some of the above comments, when I try and use ffmpeg, I get told it won't be in future releases (but it will still be available -- yay!).  avconv seems to work fine though so there's no problem.  

Just open a terminal and type 
```
avconv
```and if it says 

avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man avconv'

then you have it installed!

I haven't tried, but I'm downloading FFMPEG, see how that goes... Well, before any starts to discuss my OS, it's Ubuntu 12.04 Precise Pangolin... On a Dell Studio 1737

---

### Post by Beatsleigher on 2012-07-06
I'm too stupid to use ffmpeg -.-

I can develope for Android, flash every mobile phone, but I'm too stupid to use a command line program -.- That's somewhat sad...

Anyways, I'll give the other ones a go...

(Still pi***d off... -.-)

---

### Post by bryncoles on 2012-07-06
Bah.  You just need practice (and an unhealthy sense of masochism). 

Is it a dvd, avi, flv, vcd you are trying to extract the audio from?

---

