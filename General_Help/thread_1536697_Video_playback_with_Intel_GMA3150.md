---
title: "Video playback with Intel GMA3150"
date: 2010-07-22
forum: General Help
---

### Post by jschall1 on 2010-07-22
I'm trying to get video playing smoothly on my netbook, which is an asus 1001p with the intel gma3150 graphics chipset. I'm using kubuntu netbook edition 10.04 with the latest drivers from this ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
But still, even playing 720p in dragon player is dropping frames. In VLC it's worse, not only is the video bad, but the audio is far out of sync.

Googling turns up nothing but a news article that says "jolicloud plays 1080p video on gma3150," along with a video of VLC on jolicloud playing a 1080p video on a netbook. I don't want to use jolicloud, but I'd love to know how they got that working. I've tried emailing them, and they're just not willing to help.

News article with video: [http://www.liliputing.com/2010/02/jolicloud-adds-support-for-1080p-hd-video-on-pine-trail-netbooks.html](http://www.liliputing.com/2010/02/jolicloud-adds-support-for-1080p-hd-video-on-pine-trail-netbooks.html)
I looked up the netbook in the video and it has the same graphics as mine.

---

### Post by RJARRRPCGP on 2010-07-22
Since Karmic, frame drops shall not exist. 

Jaunty was expected to have frame drops, because of a bug with MTRR. That has been fixed since Karmic.

How would you know you're affected: 

YouTube videos, when in fullscreen, pause. (stop updating when playing and the audio still keeps going on) 
Or fullscreen YouTube videos are jerky.

---

### Post by jschall1 on 2010-07-22
Fullscreen youtube videos are jerky. So are non-fullscreen youtube videos. Hulu videos are even worse.

720p or higher videos played in dragon player (backed by xine) are jerky, 720p or higher videos played in VLC are jerky tend to get out of sync with audio, because the video is playing too slow.

---

### Post by davidmohammed on 2010-07-22
... according to this [website]("http://www.netbookchoice.com/tag/intel-gma-3150/") - intel doesnt support HD playback with your graphics set...

---

### Post by jschall1 on 2010-07-22
> **davidmohammed said:**
> ... according to this [website]("http://www.netbookchoice.com/tag/intel-gma-3150/") - intel doesnt support HD playback with your graphics set...
Aware of that.
That doesn't change the fact that that video proves it can be done assuming it's not faked.

---

### Post by RJARRRPCGP on 2010-07-22
Please post the results of ```
cat /proc/mtrr
```

---

### Post by jschall1 on 2010-07-22
> **RJARRRPCGP said:**
> Please post the results of ```
cat /proc/mtrr
```

```
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x03f700000 ( 1015MB), size=    1MB, count=1: uncachable
reg02: base=0x03f800000 ( 1016MB), size=    8MB, count=1: uncachable
reg03: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining
```

---

### Post by jschall1 on 2010-07-22
Still trying to google if this is correct. The netbook only has 1GB of ram, but
reg03: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining
says base is 3328MB? I don't understand what I'm looking at, so I don't know if it's correct or not. Is it?

---

### Post by jschall1 on 2010-07-22
Still don't understand what I'm looking at, but here's some lines from Xorg.0.log that might be relevant:
```
(--) PCI:*(0:0:2:0) 8086:a011:1043:83ac Intel Corporation N10 Family Integrated Graphics Controller rev 0, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7d00000/1048576, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:a012:1043:83ac Intel Corporation N10 Family Integrated Graphics Controller rev 0, Mem @ 0xf7e80000/524288
```

I'm going to assume the mtrr is correct, because 0xd0000000/268435456 matches up with 0x0d0000000 ( 3328MB), size=  256MB

---

### Post by davidmohammed on 2010-07-23
what makes you think that the 3150 chipset plays HD? - comments from that article state intel disabled HD H.264 playback - i.e. anything flash based.

The netbook in question is a later model with a better chipset.

---

### Post by jschall1 on 2010-07-23
> **davidmohammed said:**
> what makes you think that the 3150 chipset plays HD? - comments from that article state intel disabled HD H.264 playback - i.e. anything flash based.

The netbook in question is a later model with a better chipset.
The netbook in the video is a samsung n220 with 3150 graphics.

In addition, scroll down to "video" on this page:
[http://www.jolicloud.com/product/specifications](http://www.jolicloud.com/product/specifications)
> Full HD 1080p supported with Intel GMA 3150 and Nvidia ION video chipset

Again, I haven't tried jolicloud yet, but it sounds like they got hd video playing.

---

