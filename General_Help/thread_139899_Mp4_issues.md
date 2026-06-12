---
title: "Mp4 issues"
date: 2006-03-05
forum: General Help
---

### Post by Nikunya on 2006-03-05
I have several video files that are Mp4s.
I've tried everything I can think of to play them.  VLC almost worked but it quits after maybe a minute of two.

:(

---

### Post by mcpish on 2006-03-05
**mplayer** works really well for mp4s.  I playback a lot of .mp4 videos (MPEG-4 video with AAC audio).  

I'm not sure if the pre-compiled package in the Ubuntu repositories has all the codecs needed built into the package, I usually compile it myself.  If you compile it yourself you can add a whole bunch of extra codec support that the pre-compiled package doesn't have, like the x264 (MPEG-4 AVC) codec (which is 1 of the 2 video-codecs that mp4 files can use, the other being MPEG-4 ASP).  This might be your problem since by default, most systems don't have MPEG-4 AVC (Advanced Video Codec) support but only have the older MPEG-4 ASP (Advanced Simple Profile) which codecs such as xvid or divx are based on.

You'll need to install a **TON** of *-dev packages from Synaptic to add all the possible combinations of codecs and formats that mplayer is capable of supporting, but if you do, mplayer is by far the best media player.  The configure script for mplayer will go through and try to autodetect as many codecs as you've installed.  The **only** media format that mplayer doesn't play for me on my own compiled version of the programme is WMV version 9.  It plays everything else, Windows Media Player < 9, RealAudio/RealVideo, mp3, mp4, ogg, mkv, quicktime, mov, avi, the list goes on.  Another good thing about compiling your own version is that the Ubuntu package only supports MMX whereas mplayer is capable of detecting and fully utilizing SSE, SSE2, 3DNOW, and 3DNOW2 instruction sets on your CPU during compilation.  This will create a much more optimized binary of mplayer that will decrease your CPU utilization during video playback.

---

