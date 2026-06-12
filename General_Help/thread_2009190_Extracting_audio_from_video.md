---
title: "Extracting audio from video?"
date: 2012-06-24
forum: General Help
---

### Post by Culip on 2012-06-24
How can I **extract (not reconvert)** an audio source from a video file?

For exmaple,

video.mp4 [motionPicture.mp4 (H264) + audioSource.aac]
-> audioSource.aac

I've tried

[FONT="Courier New"]$ffmpeg -i video.mp4 audio.aac[/FONT] *# Not good. This is *recompressed and losing the quality even more!
[FONT="Courier New"]
$ffmpeg -i video.mp4 audio.flac[/FONT] *# Ok, but resulting bigger file size. Lossy to lossless sounds stupid.*
[FONT="Courier New"]
$mplayer -dumpaudio video.mp4 -dumpfile audio.aac[/FONT] *# It doesn't work (and I don't know how it actually works.) Why??*

If you have any idea, please advise. Thanks.

---

### Post by ron999 on 2012-06-24
Hi
These commands are OK:-

```
ffmpeg -i video.mp4 -vn -acodec copy audio.aac
```
or
```
ffmpeg -i video.mp4 -vn -acodec copy audio.m4a
```

---

### Post by evilsoup on 2012-06-24
ffmpeg -i input.mp4 -vn -acodec copy output.aac

The '-acodec copy' tells ffmpeg to copy the audio stream without converting; '-vn' isn't strictly necessary if you want to use AAC as the format, it tells ffmpeg to strip out the video, but since AAC is a purely audio format the program will do that automatically. If you want to be able to add metadata tags, you should use MP4 or M4A (some portable devices can play M4A but not MP4, even though they are actually the same container format but with different file extensions).

Also, if you want to put in metadata with ffmpeg, [here]("http://multimedia.cx/eggs/supplying-ffmpeg-with-metadata/") is a guide.

---

### Post by elliotn on 2012-06-24
audacity

---

### Post by Culip on 2012-06-24
Awesome, 
[FONT="Courier New"]ffmpeg -i video.mp4 -vn -acodec copy audio.aac[/FONT]
worked! I can't tell the difference between audio.aac and audio.flac though the first one has much smaller file size. Thank you, ron999! : )

To: evilsoup
Thank you so much for explaining it in detail. I will study more : )

To: elliotn
I haven't thoguht about that. That sounds more human-friendly! Thanks : )

---

