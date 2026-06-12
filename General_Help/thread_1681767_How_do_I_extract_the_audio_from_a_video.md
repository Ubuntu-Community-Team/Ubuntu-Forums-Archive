---
title: "How do I extract the audio from a video?"
date: 2011-02-04
forum: General Help
---

### Post by ninjaaron on 2011-02-04
... and encode it to an audio file?

I feel like I used to known how to do this...

---

### Post by ragtag on 2011-02-04
An easy way to do it is using the VLC video player. In the Media>Convert/Save..., menu. You can add your file, and specify the output format as audio only mp3, ogg, flac and more.

If you want to do it on the command line, that's possible too...but I don't remember how from the top of my head. :) Look at ffmpeg and mencoder.

---

### Post by ninjaaron on 2011-02-04
sounds good. I'll give it a try.

---

### Post by Malcy on 2011-02-04
Here are a couple of ways:

1. Install WinFF. Set the output to audio and choose mp3. Select the track to be converted and convert it.

2. Install kdenlive. Start a new project, import the video to the timeline. Render the track using the Audio Only option.

---

### Post by FakeOutdoorsman on 2011-02-05
FFmpeg can copy the audio from one file and put it into another without the need to re-encode. This preserves the quality. Example:

1. Investigate the file so you know what format the output should be:
```
$ ffmpeg -i IronMan.mkv
...
Stream #0.1: Audio: **aac**, 48000 Hz, stereo, s16
```

2. The audio is aac which can go into a MP4 container:
```
ffmpeg -i IronMan.mkv -vn -acodec copy output.mp4
```
The **-vn** option tells ffmpeg to ignore the video for output containers that can also include video.

---

