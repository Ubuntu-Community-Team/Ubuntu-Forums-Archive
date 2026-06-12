---
title: "converting movie files"
date: 2010-06-07
forum: General Help
---

### Post by spawn82 on 2010-06-07
hi all i am using ubuntu 9.10 just wondering what format i need to convert avi movie file to work on my sony ericsson xperia x10 if some one could help or knows more then i do that would be great thanks in advance :confused:

---

### Post by madnessjack on 2010-06-07
If you know how to use WINE, you could try seeing if this program works, looks quite promising
[http://www.aura4you.com/pmp-video-converter/Sony_Ericsson_Xperia_X10.php](http://www.aura4you.com/pmp-video-converter/Sony_Ericsson_Xperia_X10.php)

Else you could try Fuoco tools, many people have reported success converting movies with it
[http://ubuntuforums.org/showthread.php?t=776412](http://ubuntuforums.org/showthread.php?t=776412)

You're looking to convert to any of the following formats
- MP4/H.263/H.264/WMV player

Hope this helps

---

### Post by spawn82 on 2010-06-07
so i cant use devede to convert i use that programe before i burn to disc

---

### Post by madnessjack on 2010-06-07
Sorry, I wouldn't know, I've never used the software before and a quick google and a browse around their web-site isn't giving me any obvious answers.

---

### Post by derekeverett on 2010-06-07
What file format are you looking to convert to exactly?

---

### Post by howefield on 2010-06-07
Handbrake will cover several of the file formats the phone can play, just one caveat though, if you are running Ubuntu 10.04 you will need to use the nightly snapshots via the PPA here.. 

```
https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots 
```

If you are using an earlier Ubuntu release, the download from handbrake.fr should work fine.

---

### Post by spawn82 on 2010-06-07
> **derekeverett said:**
> What file format are you looking to convert to exactly?
 
Im not sure i use ubuntu 9.10 my phone is a sony ericsson xperia x10 im at work now don't finish till 11pm i can find out what file format it surports and get back to you then 
thanks heaps for every ones help :P

---

### Post by spawn82 on 2010-06-08
> **derekeverett said:**
> What file format are you looking to convert to exactly?
 
hi derekeverett i looked in to the surpported file format for my phone i could not find any info on it i beleive mp4 should work if ya could surgest a programe that would convert the file with out to much messing around would be great thanks mate for ya help 
:)

---

### Post by FakeOutdoorsman on 2010-06-08
> **spawn82 said:**
> hi all i am using ubuntu 9.10 just wondering what format i need to convert avi movie file to work on my sony ericsson xperia x10 if some one could help or knows more then i do that would be great thanks in advance :confused:

According to the [specifications](http://www.sonyericsson.com/cws/download/1/742/294/1273215984/dw-300003-WP_X10_mini_5.pdf) [PDF] (I believe this is the same or a similar device) it can handle H.264 Baseline, so the *ipod640* or *ipod320* presets in FFmpeg should work.

1. Download FFmpeg and enable additional encoders:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encode video.  Try video only first, and if it works, try with audio because the device specifications were not very helpful.  Open Terminal and enter:
```
ffmpeg -i input.foo -t 10 -an -vcodec libx264 -vpre hq -vpre ipod640 -crf 26 -threads 0 output.mp4
```
Of course **input.foo** should be the name of whatever the input file is called.  If the input video is large, you should resize it with *-s*, such as *-s 640x320*.  Notice I added *-t 10* to the example, which will create an output video that is 10 seconds long so you don't have to re-encode a huge file and wait for a long time.

If the first example does not work then try another preset:
```
ffmpeg -i input.foo -an -t 10 -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -threads 0 -s 320x240 output.mp4
```
I added *-s 320x240* to this example.  If the video-only examples work then try it with audio too:
```
ffmpeg -i input.foo -t 10 -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -threads 0 -s 320x240 -acodec libfaac -aq 100 output.mp4
```
If this works, then go ahead and remove the *-t 10* and encode the whole thing.

---

