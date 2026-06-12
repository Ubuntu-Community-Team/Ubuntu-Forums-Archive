---
title: "Record video/audio from screen"
date: 2011-08-26
forum: General Help
---

### Post by J V on 2011-08-26
I'm trying to record video/audio from screen while playing a game.


[LIST]
[*]xvidcap works very slowly and outputs the wrong framerate (Causing the video to seem speeded up) and doesn't record audio
[*]recordmydesktop has had a bug for ages that causes it to cut off part of the video
[*]ffmpeg's x11grab (My preference atm) produces a corrupted file, or doesn't record anything, the audio and video are both missing (Vlc shows a green picture, and totem throws a gstreamer error "(totem:27457): GStreamer-CRITICAL **: gst_pad_alloc_buffer_full: assertion `size >= 0' failed")
[*]as vlc and mplayer are based on ffmpeg, those won't work either
[/LIST]


I'm on debian, can someone help me get a screencapture working? (Preferably by ffmpeg)

My current attempt is:```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 25 -s hd720 -i :0.0 -vcodec huffyuv -sameq out.avi
```

---

### Post by ron999 on 2011-08-26
Hi
There's a tutorial thread here:- [http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by J V on 2011-08-26
Allright! Apparently huffyuv sucks :)

Current command is:```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 25 -s hd1080 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 -vf 'scale=-1:720' -sameq out.avi
```Audio still doesn't work :( (mp3 codec problem)

---

### Post by J V on 2011-08-26
Ok, I so far have this:```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 25 -s hd1080 -i :0.0  -vcodec libx264 -vpre lossless_ultrafast -threads 0 -vf 'scale=-1:720'  -acodec libmp3lame -sameq out.avi
```

No more errors, but I'm still not getting any sound (I get sound from webcam on different device input though)

I'm going to presume it's something I have muted in alsa, what could it be?

---

### Post by dodle on 2012-05-04
I know this thread is old but I found a solution that works for me and wanted to share. Here is part of a script that I wrote:

```
nohup ffmpeg -y -f x11grab -r 30 -s 1280x800 -i :0.0 -sameq -vcodec libx264 /tmp/video.tmp.avi > /tmp/nohup$$.out 2>&1 &

P1=$!

ffmpeg -y -f alsa -i hw:0,0 -acodec libmp3lame -ac 1 -ar 44100 -ab 128k /tmp/audio.tmp.mp3
  
/bin/kill -s INT $P1
  
ffmpeg -i /tmp/video.tmp.avi -i /tmp/audio.tmp.mp3 -vcodec copy -acodec copy $1.avi

if [ "$?" -eq 0 ]
then
  rm /tmp/video.tmp.avi /tmp/audio.tmp.mp3
else
  echo "Muxing error, temporary files have not been deleted from /tmp"
fi
```

---

### Post by KubaLibre on 2012-05-04
you are best!

---

