---
title: "Video Playing Software"
date: 2006-06-09
forum: General Help
---

### Post by GmAz on 2006-06-09
I need a video playing software that will play MPG files as well as WMV files.  I have a lot of videos of my baby I made from WinXP and I need something that can play them.  I have tried MPlayer which only plays about half my MPGs and no WMV files.  Same with VLC Media Player.  Is there at least a way to download the codec to play those files in one of those programs?

---

### Post by lkagan on 2006-06-09
First you need to understand that Totem and Xine (I believe) both use gstreamer as the workhorse that does the video decoding and playback.  That being said, you need to supply the correct codecs to gstreamer.  I did that and can play wmv vids.  More info can be found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=157000&page=2&highlight=wmv+files").

Good Luck!

Larry

---

### Post by ephman on 2006-06-09
hi,

i really think if you compile mplayer from source with the win32 codecs it's the finest quality video player.  but that just might be my eyes.

this should help you out.
[http://ubuntuforums.org/showthread.php?t=187709&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=187709&highlight=mplayer)

thanks for the bandwidth,
ephman

---

