---
title: "Can't Play 10bit Videos"
date: 2011-11-02
forum: General Help
---

### Post by Kissell on 2011-11-02
I installed Ubuntu 11.10 as a fresh install, and can't play 10bit video.  

10-bit video compression is fairly new, but a good thing, you get better quality using less bitrate.  I already have several 10bit videos that played just fine under Windows 7 (after installing a codec pack).

In Ubuntu I have installed VLC player and mplayer2, but neither of them came with a codec that can play 10bit video.  The audio plays in VLC, but I just get a green screen for the video.  

Anyone know how to fix this problem in Ubuntu?  I couldn't find a thread about it on here, so I'm thinking perhaps there isn't yet an easy way to just install a codec or something through the repositories.

---

### Post by WorMzy on 2011-11-02
You possibly need a newer version of ffmpeg, or mplayer2, or both. Have a poke around on Launchpad and see what you can find.

---

### Post by andrew.46 on 2011-11-03
> **Kissell said:**
> I already have several 10bit videos that played just fine under Windows 7 (after installing a codec pack).

Can you post one of these somewhere? I would be interested to have a look at one...

---

### Post by Kissell on 2011-11-03
You can do a search at [http://nyaa.eu]("http://nyaa.eu") for "10bit".  There are several torrents posted there.  Anime Fansubbers seem to be the only ones going full speed ahead into 10-bit video compression.

The one I was trying to watch was this week's episode of Bleach.  There are no subtitles on TV, so I was trying to watch the torrent which has English subtitles.  After hours trying different codecs and media players from the mediabuntu repositories, I finally just watched the 8-bit version.

[http://www.nyaa.eu/?page=torrentinfo&tid=257270]("http://www.nyaa.eu/?page=torrentinfo&tid=257270")

---

### Post by andrew.46 on 2011-11-03
Interesting, FFmpeg certainly identifies the 10bit video of that Bleach episode:

```

Stream #0:1(eng): **[COLOR="Red"]Video: h264 (High 10)[/COLOR]**, yuv420p10le, 1280x720 [...]

```

and the good news is that the svn MPlayer plays this back with no problems, I attach a screenshot of the commandline player in action as well as UMPlayer, in case you are more gui minded :).

---

### Post by Kissell on 2011-11-03
Thanks.  UMplayer isn't in the repositories, but I went to their website and downloaded the .deb file.  It does allow me to play 10bit videos.  Yatta!!

---

### Post by andrew.46 on 2011-11-03
> **Kissell said:**
> Thanks.  UMplayer isn't in the repositories, but I went to their website and downloaded the .deb file.  It does allow me to play 10bit videos.  Yatta!!

Great news :). UMPlayer is of course a front-end for MPlayer so perhaps the repository MPlayer is enough for 10bit media (I am assuming that the website UMPlayer is using the repository MPlayer). But anyway: Enjoy your movie!

**Edit:** BTW, stimulated by this thread I have investigated a little and created my own 10bit video from an episode of the Matrix movie. Check it out if you are interested:

```

wget http://www.andrews-corner.org/tmp/matrix_sparring_h10.mkv

``` 

Needs a little tweaking but the basics are in place :).

---

