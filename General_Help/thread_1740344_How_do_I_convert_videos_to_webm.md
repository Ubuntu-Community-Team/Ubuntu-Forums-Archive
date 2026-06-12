---
title: "How do I convert videos to webm?"
date: 2011-04-26
forum: General Help
---

### Post by Dustin2128 on 2011-04-26
I've got a rather large collection of videos that I'm going to need to reencode in webm or theora from mp4, flv, etc. How would I do that with little/no quality loss?

---

### Post by papibe on 2011-04-27
I believe that the latest version of VLC can decode and encode webm. I'm not clear how to get it though.

I hope it helps.

---

### Post by andrew.46 on 2011-04-27
> **Dustin2128 said:**
> I've got a rather large collection of videos that I'm going to need to reencode in webm or theora from mp4, flv, etc. How would I do that with little/no quality loss?

Best to use FFmpeg and libvpx 0.9.6, follow this guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and think about adding in the presets patch [here]("http://code.google.com/p/webm/downloads/list"). I have been mucking around with webm a little just recently and my best effort is here:

```
wget http://www.andrews-corner.org/tmp/matrix_sparring.webm
```

but I am far from an expert and I am sure my effort could easily be improved upon :). And of course as Papibe has mentioned a recent vlc can also output webm...

---

### Post by papibe on 2011-05-08
I just wanted to share what I recently discovered as an alternative to ffmpeg and WinFF. There's an application in the repositories called Arista Transcoder. It does webm transcoding, and have several useful presets, like iPod, Android, etc.

Moreover, here's a review/tutorial [video]("http://www.jupiterbroadcasting.com/5068/how-to-encode-webm-bsd-tips-las-s15e05/") from the "Linux Action Show" of JupiterBroadcasting.com (just watch the first 10mins, later it gets into another turorial).

Regards.

---

