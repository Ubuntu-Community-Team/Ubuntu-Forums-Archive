---
title: "Recordmydesktop output is nonsense..."
date: 2011-01-12
forum: General Help
---

### Post by J V on 2011-01-12
While totem and VLC can easily play this file created by recordmydesktop, windows can't (As it's theora)

Unfortunately, nothing I have will convert it. Mencoder, VLC, ogv2avi, handbrake, kdenlive, pitivi, openshot, NOTHING seems able to convert this file's format.

I have uploaded a demo for you to try yourself and maybe discover what's wrong with it. rmd worked fine last time I used it (Although that was back in jaunty so...)

PS: Why is this file normally 30k but in a tar it's 40k? :/

---

### Post by ron999 on 2011-01-12
Hi
There's nothing wrong with the file.

Try converting again using a command like this:-

```
mencoder out.ogv -o output.avi -ovc lavc -oac mp3lame
```

---

### Post by JohnAStebbins on 2011-01-12
> **J V said:**
> While totem and VLC can easily play this file created by recordmydesktop, windows can't (As it's theora)

Unfortunately, nothing I have will convert it. Mencoder, VLC, ogv2avi, handbrake, kdenlive, pitivi, openshot, NOTHING seems able to convert this file's format.

I have uploaded a demo for you to try yourself and maybe discover what's wrong with it. rmd worked fine last time I used it (Although that was back in jaunty so...)

PS: Why is this file normally 30k but in a tar it's 40k? :/

ffmpeg seems to think this file has no keyframes.  I don't know about the other encoders, but HandBrake attempts to seek to the first keyframe before starting an encode.  If there aren't any, it reaches the end of the file and decides there is nothing useful to encode.

---

### Post by FakeOutdoorsman on 2011-01-12
FFmpeg for Maverick 10.10 has no problem with this video, but FFmpeg from older Ubuntu versions will not decode it properly. This is because a bug was fixed and FFmpeg from releases older than Maverick are too old to include the bug fix.

If you want to use FFmpeg to convert the video and are using an Ubuntu release that's older than Maverick you can compile a recent FFmpeg. It's fairly straightforward with these instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

> **J V said:**
> While totem and VLC can easily play this file created by recordmydesktop, windows can't (As it's theora)
VLC is also available for Windows.

---

### Post by J V on 2011-01-13
Would there be a PPA for the latest FFMPEG on lucid?

---

### Post by FakeOutdoorsman on 2011-01-13
I don't know of a PPA that contains FFmpeg for Lucid, but I'm not a big fan of PPAs anyway so I haven't been paying too much attention.

What's wrong with compiling? That guide is a simple copy and paste procedure.

---

### Post by FakeOutdoorsman on 2011-01-13
I don't know of a PPA that contains FFmpeg for Lucid, but I'm not a big fan of PPAs anyway so I haven't been paying too much attention.

What's wrong with compiling? That guide is a simple copy and paste procedure.

---

### Post by Primefalcon on 2011-01-13
> **J V said:**
> While totem and VLC can easily play this file created by recordmydesktop, windows can't (As it's theora)

Unfortunately, nothing I have will convert it. Mencoder, VLC, ogv2avi, handbrake, kdenlive, pitivi, openshot, NOTHING seems able to convert this file's format.

I have uploaded a demo for you to try yourself and maybe discover what's wrong with it. rmd worked fine last time I used it (Although that was back in jaunty so...)

PS: Why is this file normally 30k but in a tar it's 40k? :/
try install arista transcoder for an easy to use converter

an easy cli way is also 

```
ffmpeg -i videoToConvert.ogv -sameq outputFile.mp4
```
the sameq command tells it to keep it the same quality, you may have to install ffmpeg first via sudo apt-get install ffmpeg

---

### Post by 0N3 on 2011-01-13
WinFF should convert it no problem

---

### Post by Primefalcon on 2011-01-13
> **0N3 said:**
> WinFF should convert it no problem
I have had issues with winFF here and there IMO better to just use ffmpeg direct or arista transcoder

---

### Post by FakeOutdoorsman on 2011-01-13
> **Primefalcon said:**
> 
```
ffmpeg -i videoToConvert.ogv -sameq outputFile.mp4
```
the sameq command tells it to keep it the same quality, you may have to install ffmpeg first via sudo apt-get install ffmpeg
That's not how the *-sameq* option works. sameq only works in some situations, such as when where the input and output have valid quantizer scales in the same range. For example, Theora and MPEG-4 do not have the same quantizer scale.  Also, quality and quantizer are only loosely correlated.

It's confusing especially because the documentation (*ffmpeg -h*) isn't very clear.

> **0N3 said:**
> WinFF should convert it no problem

WinFF uses FFmpeg to convert. FFmpeg from Ubuntu versions older than Maverick will not decode videos from certain versions of recordMyDesktop.

---

### Post by ben2talk on 2011-02-15
Well then all I can say is that there's a huge problem when you can't do this without installing command line software and use complicated commands instead of just dropping the file into Openshot or something similar.

Recordemydesktop output is nonsense. It should be easily configured to give an output of something simple - avi, mp4, or whatever - something that ANY video player can handle and that can be uploaded to youtube.

This is not just my opinion. Ask just about anyone who uses computers who isn't trying to support Ubuntu (don't even mention the OS) and they'll tell you - it's a non-starter.

---

