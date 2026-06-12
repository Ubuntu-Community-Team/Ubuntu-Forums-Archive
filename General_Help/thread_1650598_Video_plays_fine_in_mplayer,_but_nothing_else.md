---
title: "Video plays fine in mplayer, but nothing else"
date: 2010-12-21
forum: General Help
---

### Post by azredwing on 2010-12-21
Hi all,

Got this weird problem. I just installed 10.10 to my Thinkpad W510. I am trying to install the proper codecs required to play .avi and other files. I can hear sound, but no video.

I can play videos just fine using mplayer, but not totem.

Any ideas how to fix? Thanks!

---

### Post by papibe on 2010-12-22
Totem is a fine player, but no matter how many codecs you install, mplayer will always play more formats that Totem. The same goes with VLC (another player with codecs "included").

If I were you, I would install smplayer (nice interface to use mplayer) and/or install VLC. Between smplayer and VLC you'll be covering almost any video and audio format.

Regards.

---

### Post by azredwing on 2010-12-22
> **papibe said:**
> Totem is a fine player, but no matter how many codecs you install, mplayer will always play more formats that Totem. The same goes with VLC (another player with codecs "included").

If I were you, I would install smplayer (nice interface to use mplayer) and/or install VLC. Between smplayer and VLC you'll be covering almost any video and audio format.

Regards.

Hi **papibe**:

VLC doesn't work; interestingly, neither does smplayer. Audio plays, but no video. I am so confused right now. Thanks for the input, though.

---

### Post by sikander3786 on 2010-12-22
I would recommend to try installing ubuntu-restricted-extras if not already installed.

```
sudo apt-get install ubuntu-restricted-extras
```

It comes with nearly all the needed audio/video codecs, flash, open source java and some fonts. Lets see how that goes.

---

### Post by azredwing on 2010-12-22
> **sikander3786 said:**
> I would recommend to try installing ubuntu-restricted-extras if not already installed.

```
sudo apt-get install ubuntu-restricted-extras
```

It comes with nearly all the needed audio/video codecs, flash, open source java and some fonts. Lets see how that goes.

Hi **sikander3786**,

Already installed. That was the first thing I did when I got this computer set up, actually. Thanks for the help, though.

---

### Post by papibe on 2010-12-22
> **azredwing said:**
> ...
VLC doesn't work; interestingly, neither does smplayer. Audio plays, but no video...

Interesting... I wonder how the video was encoded in that file. If you use VLC to play the file, you can see the codec information by going to Toos -> Codec Information. What does it say?

Regards.

---

### Post by azredwing on 2010-12-22
> **papibe said:**
> Interesting... I wonder how the video was encoded in that file. If you use VLC to play the file, you can see the codec information by going to Toos -> Codec Information. What does it say?

Regards.

Playing a .avi file:

```

Stream 0
    Type: Video
    Codec: MPEG-4 Video (XVID)
    Resolution: 512x384
    Frame rate: 23.976000
Stream 1
    Type: Audio
    Codec: MPEG Audio layer 1/2/3 (mpga)
    Channels: Stereo
    Sample rate: 48000 Hz
    Bitrate: 128 kb/s

```

Somehow, .MOV files are working properly in VLC. They weren't last night. Maybe it was a one-time thing. I'll keep trying.

EDIT: One-time thing. The same .mov file I was playing for doesn't work anymore with VLC. Nothing still works with totem or smplayer, but again all videos are working correctly with mplayer.

---

### Post by azredwing on 2010-12-25
Found a solution at [http://www.linuxquestions.org/questions/ubuntu-63/10-04-totem-sound-but-no-video-problem-[solved]-838222/](http://www.linuxquestions.org/questions/ubuntu-63/10-04-totem-sound-but-no-video-problem-[solved]-838222/) : 

> 
Thought I would post this up here, because I've been searching for a solution, and not found one online:

Problem description
When playing both .mp4 and .rm files, the sound played fine, but the display remained black.

Solution
Open the Configuration Editor (run gconf-editor in the terminal). Navigate to system > gstreamer > 0.10 > default, double-click on videosink and change the setting from autovideosink to ximagesink 

Worked for me.


Posting here so others may find it..

---

