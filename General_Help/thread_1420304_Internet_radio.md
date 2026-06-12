---
title: "Internet radio"
date: 2010-03-02
forum: General Help
---

### Post by jeffrey2009 on 2010-03-02
Does anyone know how I can play the following URL in a mdeia player on ubuntu.

[http://82.135.234.195/pukas2.wax](http://82.135.234.195/pukas2.wax)

I looked into Rythmbox and Songbird so far and could not get it to work.  I am trying to cutover to Ubuntu and this is one of my requirements.

---

### Post by emanuel.b on 2010-03-02
You should try VLC media player. If that doesn't work, use RealPlayer...

[http://www.videolan.org]("http://www.videolan.org/")

[http://www.real.com]("http://www.real.com/")

---

### Post by mc4man on 2010-03-03
vlc works here but I fear you may  have some issues, the stream appears to be wma3 (pro), which the repo vlc doesn't support. (nor most other players 

Your best bet may Amarok ( though on karmmic I use the amarok 1.4 redo - pana), which will work if you're on a  32 bit install thru w32codecs as will a ppa or self built mplayer 

(mplayer will decode this on both 32 and 64 bit thru libavcodec and has a couple of good frontends - smplayer and gnome-mplayer

It can easily be added as a radio station in amarok,( or pana) as seen in screen or by making a .m3u to load.
```
#EXTM3U
#EXTINF:0,Pukas 2
mms://82.135.234.199/Pukas2?MSWMExt=.asf

```


realplayer may also work, I only had it installed once quite some time ago, never used and found it annoying when it took over all the audio icons, among other things

---

### Post by jeffrey2009 on 2010-03-03
install amarok put could not add the playlist.    I think I have another version and need to play around some more.

---

