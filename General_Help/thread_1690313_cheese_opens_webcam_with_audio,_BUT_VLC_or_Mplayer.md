---
title: "cheese opens webcam with audio, BUT VLC or Mplayer cant"
date: 2011-02-18
forum: General Help
---

### Post by sdowney717 on 2011-02-18
so far only cheese works with the webcam. cant seem to get anything else to work including skype ekiga, nada.
so how to open in mplayer or vlc ?

cheese DOES WORK FINE, regardless of these errors.
> scott@scott-desktop:~$ cheese /dev/video1

(cheese:2263): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

** (totem-video-thumbnailer:2291): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:2291): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:2291): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:2291): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:2291): WARNING **: Could not take screenshot: no video info
totem-video-thumbnailer couldn't get a picture from 'file:///home/scott/Videos/Webcam/2011-01-07-124826.ogv'

** (cheese:2263): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-124826.ogv (video/ogg)




---

### Post by sdowney717 on 2011-02-18
[http://old.nabble.com/Bug-535278%3A-vlc%3A-crash-adding-a-second-webcam-td27665679.html](http://old.nabble.com/Bug-535278%3A-vlc%3A-crash-adding-a-second-webcam-td27665679.html)

following this I can get it to play on VLC using
vlc v4l2:///dev/video0

mplayer wont work with that
scott@scott-desktop:~$ mplayer v4l2:///dev/video0 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing v4l2:///dev/video0.
No stream found to handle url v4l2:///dev/video0


Exiting... (End of file)
scott@scott-desktop:~$

---

