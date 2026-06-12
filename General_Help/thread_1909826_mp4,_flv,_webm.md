---
title: "mp4, flv, webm?"
date: 2012-01-16
forum: General Help
---

### Post by Matrix01 on 2012-01-16
which format do u use when u download a video in youtube?

---

### Post by doorknob60 on 2012-01-16
I use whichever is the highest quality as determined by youtube-dl. For HD videos it's usually MP4, but some non HD videos the FLV is higher quality, so it grabs that. It never gets the WebM for whatever reason, but that's not a problem, as long as it gets the best quality one :)

EDIT: This thread may be borderline breaking the forums rules as of a recent change: [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

### Post by Matrix01 on 2012-01-16
how do u find whether viedo clip is HD or not? 

> **doorknob60 said:**
> I use whichever is the highest quality as determined by youtube-dl. For HD videos it's usually MP4, but some non HD videos the FLV is higher quality, so it grabs that. It never gets the WebM for whatever reason, but that's not a problem, as long as it gets the best quality one :)

EDIT: This thread may be borderline breaking the forums rules as of a recent change: [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

### Post by WasMeHere on 2012-01-18
> **Matrix01 said:**
> how do u find whether viedo clip is HD or not?
HD, High Definition is a general term for high quality video, usually big frame size, 1280x720 or 1920x1080 pixels and high frame rate, 30, 50 or 60 Hz. 1920x1080 is sometimes called full HD. See the following link
[[COLOR="RoyalBlue"]_http://en.wikipedia.org/wiki/High-definition_video_[/COLOR]]("http://en.wikipedia.org/wiki/High-definition_video")

---

### Post by andrew.46 on 2012-02-21
youtube-dl has an option that only works with youtube that actually does not violate either the YouTube TOS or this Forum's rules:

```

andrew@skamandros~$ youtube-dl **[COLOR="Red"]--list-formats[/COLOR]** 'http://www.youtube.com/watch?v=YEJIrat4hS0'
[youtube] Setting language
[youtube] YEJIrat4hS0: Downloading video webpage
[youtube] YEJIrat4hS0: Downloading video info webpage
[youtube] YEJIrat4hS0: Extracting video information
Available formats:
35	:	flv	[480x854]
44	:	webm	[480x854]
34	:	flv	[360x640]
18	:	mp4	[360x640]
43	:	webm	[360x640]
5	:	flv	[240x400]

```

Not sure when this option became available but it is certainly available in the most recent version:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl --version[/COLOR]**
2012.01.08b


```

---

### Post by wildmanne39 on 2012-02-21
Hi, it is against forum policy to download or discuss downloading youtube videos.
Thanks

---

