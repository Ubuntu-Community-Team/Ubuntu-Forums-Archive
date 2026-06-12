---
title: "Can not record video from Logitech Webcam Pro 9000"
date: 2009-09-17
forum: General Help
---

### Post by dannyman on 2009-09-17
Hello,

I have been trying all sorts of things over here, to no avail.

However, Skype works fine for sending and receiving video and audio.

Cheese and mplayer can show me video.  mencoder can record video without audio.  Hitting "Record" in Cheese causes the video to go black, and Cheese to lock up.

Here's mencoder:

```
136-13:25 djh@noneedto tmp$ **mencoder -v tv:// -tv driver=v4l2:width=960:height=720:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi|tail -10**
v4l2: ioctl get standard failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
ioctl dsp getblocksize: 0
blocksize: 16384
v4l2: set audio samplerate: 44100
v4l2: get audio format: 9
==> Found audio stream: 0
v4l2: get audio samplerate: 44100
v4l2: get audio samplesize: 2
v4l2: get audio channels: 2
  TV audio: 2 channels, 16 bits, 44100 Hz
Audio capture - buffer 256 blocks of 16384 bytes, skew average from 16 meas.

```

The big hitch seems to be audio . . .

---

### Post by NightwishFan on 2009-09-17
Do you have Pulse set to record audio or alsa? To check go to System -> Preferences -> Sound. Try GNOME sound recorder or Audacity to see if audio recording works. You can also run tests by pressing alt+f2 and typing:
```
gstreamer-properties
```
Then you can test different elements for cheese (which uses gstreamer).

---

