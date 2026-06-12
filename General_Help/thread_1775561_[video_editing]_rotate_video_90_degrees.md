---
title: "[video editing] rotate video 90 degrees"
date: 2011-06-04
forum: General Help
---

### Post by nbv4 on 2011-06-04
I have a video that I had to record with the camera sideways. I now need to rotate the video 90% so the video plays right. I tried Kimo and Pitivi, but neither of them do video rotation for some reason (or at least I couldn't figure out how). Anyone have any suggestions on a simple program that runs on Natty that will rotate video 90 degrees?

---

### Post by tgm4883 on 2011-06-04
> **nbv4 said:**
> I have a video that I had to record with the camera sideways. I now need to rotate the video 90% so the video plays right. I tried Kimo and Pitivi, but neither of them do video rotation for some reason (or at least I couldn't figure out how). Anyone have any suggestions on a simple program that runs on Natty that will rotate video 90 degrees?

It's not a often requested feature, so that is why these programs likely can't do that. You might be able to get ffmpeg to do it though, as that is usually pretty powerful.

---

### Post by coldraven on 2011-06-05
VLC seems to be the answer.
[http://www.howtogeek.com/howto/14751/rotate-a-video-90-degrees-with-vlc-or-windows-live-movie-maker/](http://www.howtogeek.com/howto/14751/rotate-a-video-90-degrees-with-vlc-or-windows-live-movie-maker/)

---

### Post by nbv4 on 2011-06-05
> **coldraven said:**
> VLC seems to be the answer.
[http://www.howtogeek.com/howto/14751/rotate-a-video-90-degrees-with-vlc-or-windows-live-movie-maker/](http://www.howtogeek.com/howto/14751/rotate-a-video-90-degrees-with-vlc-or-windows-live-movie-maker/)

"if you simply want to rotate the video while you watch it, we’ll show you how to accomplish that with VLC Media Player. If you want to convert the video so it is rotated permanently, we’ll show you how to do that with Windows Live Movie Maker and output your video as a WMV file."

:(

---

### Post by FakeOutdoorsman on 2011-06-05
FFmpeg can do this as tgm4883 mentioned, but you will need to compile it yourself first because the repository version (as of Natty) does not include filters. Compiling FFmpeg is easy with these instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Example. This will rotate the video 90 degrees clockwise, encoded as H.264 video in MKV container. The audio will simply be copied (no audio re-encoding):
```
ffmpeg -i input -vcodec libx264 -preset medium -crf 24 -threads 0 -vf transpose=1 -acodec copy output.mkv
```
More info on the transpose filter can be found in with the *man ffmpeg* command.

---

### Post by rachel1.0 on 2011-12-07
I was also looking for a way to do this and found this other thread which solved my problem: [http://ubuntuforums.org/showthread.php?t=825971](http://ubuntuforums.org/showthread.php?t=825971)

avidemux worked like a charm to me.

---

