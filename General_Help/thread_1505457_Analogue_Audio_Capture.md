---
title: "Analogue Audio Capture?"
date: 2010-06-09
forum: General Help
---

### Post by Jake007g on 2010-06-09
First off, I'd like to say please excuse my poor terminology, I'm a slight noob in this field :-)

Anyway, so I've got an easyCAP analogue capture device. It has three component cables (Red, white and yellow) on one end, and USB on the other end.

I've managed to install some video drivers and make a menCODER script to get the video to record perfectly. Now, I need some assistance in getting the audio to record. I haven't (and not sure if I need to) installed any audio drivers.

This is the current menCODER script I'm using, which only records video (And a buzzing/hissing audio sound):

> mencoder tv:// -tv driver=v4l2:width=720:height=480:device=/dev/video0:forceaudio:adevice=/dev/dsp:immediatemode=0:audiorate=44100:input=1:norm=PAL-60 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts mode=2 -o Recording

I also tried ALSA inputs at one point:
> mencoder tv:// -tv driver=v4l2:width=720:height=480:device=/dev/video0:forceaudio:alsa:adevice=hw.1:immediatemode=0:audiorate=44100:input=1:norm=PAL-60 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts mode=2 -o Recording


I have absolutely no idea how to get the audio to record. 

ANY help what so ever will be greatly appreciated

-Jake

---

### Post by lisati on 2010-06-09
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1505458](http://ubuntuforums.org/showthread.php?t=1505458)

Please do not start multiple threads for the same question. 

If you accidentally post in the wrong place, you can use the "Report" button, asking the staff to move a thread to a more appropriate place.

---

