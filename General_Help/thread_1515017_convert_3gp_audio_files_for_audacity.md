---
title: "convert 3gp audio files for audacity"
date: 2010-06-21
forum: General Help
---

### Post by xdevnull on 2010-06-21
I have an android phone.  The voice recorder records files in 3gp audio only format.  I can play these on my computer with the standard gnome player and with vlc.  However, audacity won't open it up.  There is an error that says that FFmpeg should import it but it didn't understand the format.  I need to edit some of these audio files for use.

Any help?  Is there a way to convert these files to mp3 or flac so I can edit them?  Searches turn up w32 ware and some arcane mencoder commands but they have to do with converting video.

Thanks..

---

### Post by swiftsam on 2010-10-23
Did you ever figure this out?  I'm trying to do exactly the same thing with audio from the Voice Recorder android app.

I've successfully used ffmpeg to convert the 3gp to avi but audacity doesn't want video files.   I'm sure ffmpeg is capable, I'm just too familiar yet.  anyone?

this is the code I got to work to make it into an avi, but there is no video to transcode, so this is a bit roundabout.
```
ffmpeg -i filename.3gp -f avi -vcodec xvid -acodec ogg -ar 22050 newfilename.avi

```

---

### Post by Verbeck on 2010-10-23
try using _sound converter_. its in the software centre

---

### Post by swiftsam on 2010-10-23
Wow, thank you so much.  I hate when the solution is so easy I feel stupid, but it's also really awesome.  18 seconds later, the job is done.

---

### Post by xdevnull on 2010-10-23
I'm using the Android app Hertz to record audio now instead of the google app.  I think I tried sound converter a while back without much success - but that was quite a while ago.

---

### Post by andrew.46 on 2010-10-25
There could be some confusion as I believe the android phones can put either aac or amr sound in a 3gp container. See the following:

Android Supported Media Formats
[http://developer.android.com/guide/appendix/media-formats.html](http://developer.android.com/guide/appendix/media-formats.html)

So the approach would be a little different in each case...

Andrew

---

