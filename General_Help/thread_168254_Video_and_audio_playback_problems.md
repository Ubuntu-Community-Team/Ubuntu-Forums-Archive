---
title: "Video and audio playback problems"
date: 2006-04-30
forum: General Help
---

### Post by chainzz on 2006-04-30
This is my first post so the first thing I want to say is that Ubuntu is great and I want to thank all those people who made this distro and the people who wrote all the great documentation on the internet about Linux and Ubuntu, I have already learned a lot from it.

I'm very happy with Ubuntu 5.10 Breezy Badger, and I can't wait for Dapper to be released. But I have a problem that really needs to be fixed. I have many problems playing audio and video files in Ubuntu. Both MPlayer and VLC are not working very well for me. I really want to use one of them because I don't really like Totem. I have installed all the gstreamer packages and I also installed the fglrx driver for ATI to enable 3D acceleration (I also want to play games on Ubuntu).

MPlayer's performance is very bad on my PC, the video is playing on I think 60-70% of the speed of the audio (the audio is playing on normal speed) so they get out of sync immediatly. I also tried to select other video drivers in MPlayer but only 'X11 (XImage/Shm)' is working for me, when I select other drivers Mplayer says it can't initialize the selected video_out device. With 'X11 (XImage/Shm)' I also can't play the video's fullscreen, it just stays the same size with black around it.

VLC is also not working very well for me, when I open a video or audio file with VLC I first have to select the audio track manually to make the audio work. In VLC the other video drivers do work by the way, I'm succesfully playing video files with OpenGL output, in MPlayer this isn't possible.

I also tried to use XMMS to play audio files, most of the times it works but sometimes when I open a file it says 'Couldn't open audio' and that I have to check my soundcard etc.

I hope these problems can be solved because then Ubuntu is perfect for me!

---

### Post by xyz on 2006-04-30
Hi-glad you're enjoying Ubuntu!
Try this- It did me lots of good-Do read all the way through the thread. Godd luck.
[http://ubuntuforums.org/showthread.php?t=160070&highlight=patrick](http://ubuntuforums.org/showthread.php?t=160070&highlight=patrick)

---

### Post by chettyk on 2006-04-30
I found **[Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats")** very useful in setting up my multimedia system. 

I use XMMS. Once in a while, when I choose a directory where I want all the music files played, XMMS gives me an error message to the effect that the sound card was being used by another program. I then choose a single music file to play and everything works well subsequently.

---

### Post by rez on 2006-05-02
hmm. i'm recently encountered issues myself.

i installed the w32codecs as per the restricted formats ... they worked fine for a bit.  was able to watch everything i was after.

now i get video, but no sound.  mp3s and other sounds play fine, just all the video formats won't play sound.  i'm using Mplayer and have tried many of the options ... but it just changed itself and now i'm stuck :(

---

