---
title: "Encoding videos for Youtube?"
date: 2010-08-13
forum: General Help
---

### Post by Blzut3 on 2010-08-13
Can anyone recommend a way to encode a video for youtube?  My source video is a theora/vorbis ogg, however when uploaded to youtube it is displayed as a completely green video (audio works fine).

I've tried re-rendering with different codecs through PiTiVi, however most of them hang at the first frame displaying "rendering" (a common problem from what I can tell, although I couldn't find a solution).

Converting it to an avi with mencoder causes the audio to go out of sync and the video to be shortened by about 1 minute.

I've also tried compiling ffmpeg and re-encoding to webm.  However, like all other videos I've re-encoded (webm or otherwise) with ffmpeg, the video doesn't play back at a consistent speed (slows down and speeds up randomly).

---

### Post by FakeOutdoorsman on 2010-08-14
Personally, I would [compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) and then use something like this command:
```
ffmpeg -i input.ogv -acodec copy -vcodec libx264 -vpre fast -crf 22 -threads 0 output.mkv
```

Other people recommend using MEncoder instead as shown here:
[HOWTO: Convert ogv to avi and upload to youtube](http://ubuntuforums.org/showthread.php?t=1501566)

So if one method doesn't work you can try the other.  One good thing about Linux is that there is usually several ways to tackle a problem.

I'm guessing your video is from recordMyDesktop.  This is been causing issues for many users because either recordMyDesktop is outputting non-standard OGV, or the problem was on FFmpeg's side.  Fortunately, it's already been fixed on FFmpeg, but unfortunately FFmpeg in the Ubuntu repository is too old to take advantage of this fix (unless you're using Ubuntu Maverick).  That's why I recommended compiling FFmpeg.

Another option to using recordMyDesktop is this:
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by no2498 on 2010-08-14
if you use cheese you get the ogg file type

you can use this program and get an avi file type
wxcam

---

### Post by Blzut3 on 2010-08-14
> **FakeOutdoorsman said:**
> Personally, I would [compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) and then use something like this command:
```
ffmpeg -i input.ogv -acodec copy -vcodec libx264 -vpre fast -crf 22 -threads 0 output.mkv
```
When compiling ffmpeg with x264 I get the following errors:
```
/home/blzut3/Code/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_frame':
/home/blzut3/Code/ffmpeg/libavcodec/libx264.c:92: undefined reference to `x264_picture_init'
/home/blzut3/Code/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_init':
/home/blzut3/Code/ffmpeg/libavcodec/libx264.c:300: undefined reference to `x264_encoder_open_104'
```
Even then I tried encoding in vp8/webm and the video slows down and speeds up repeatedly.  I've had the exact same problem with ffmpeg in the past when encoding a video for my PSP.

> **FakeOutdoorsman said:**
> Other people recommend using MEncoder instead as shown here:
As I said mencoder drops a whole bunch of frames causing the video to be shortened and the audio to go out of sync.

> **FakeOutdoorsman said:**
> I'm guessing your video is from recordMyDesktop.  This is been causing issues for many users because either recordMyDesktop is outputting non-standard OGV, or the problem was on FFmpeg's side.  Fortunately, it's already been fixed on FFmpeg, but unfortunately FFmpeg in the Ubuntu repository is too old to take advantage of this fix (unless you're using Ubuntu Maverick).  That's why I recommended compiling FFmpeg.
Actually I recorded an mpg using VLC from my HDTV Wonder.  Then imported the video into PiTiVi in order to add in my audio track (recorded with Audacity).  VLC can't transcode the ogv from PiTiVi into an mpg for some reason, and PiTiVi hangs unless I use ogg.

I did find a solution though.  I downloaded the latest Ubuntu 10.10 alpha and installed it in a VM.  Through there I was able to render my PiTiVi project into webm.

Thanks for the help, though if you have any idea on the ffmpeg issue I would still like to know for future reference.

---

### Post by FakeOutdoorsman on 2010-08-15
> **Blzut3 said:**
> When compiling ffmpeg with x264 I get the following errors:
```
/home/blzut3/Code/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_frame':
/home/blzut3/Code/ffmpeg/libavcodec/libx264.c:92: undefined reference to `x264_picture_init'
/home/blzut3/Code/ffmpeg/libavcodec/libavcodec.a(libx264.o): In function `X264_init':
/home/blzut3/Code/ffmpeg/libavcodec/libx264.c:300: undefined reference to `x264_encoder_open_104'
```

Did you follow this guide?  If yes, did you modify any of the commands, or did you follow it word-for-word?

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You most likely have an old x264 or libx264-dev installed.

---

### Post by Blzut3 on 2010-08-15
> **FakeOutdoorsman said:**
> You most likely have an old x264 or libx264-dev installed.
Apparently that was the case.  The video encoded in x264 by ffmpeg seems to be smooth as well. :)  Thanks again for the help.

---

