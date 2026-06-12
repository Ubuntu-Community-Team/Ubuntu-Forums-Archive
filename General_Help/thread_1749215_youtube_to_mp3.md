---
title: "youtube to mp3"
date: 2011-05-04
forum: General Help
---

### Post by soulcat on 2011-05-04
hi

what is the best program or method to download mp3 extracts from youtube to my pc

regards

ubuntu 10.10

---

### Post by neotifa on 2011-05-04
Try Miro, i believe there is a download option from any site that has a video.

Also search for a program in synaptic for youtube downloader something must be shown.
Cheers

---

### Post by ikt on 2011-05-04
> **soulcat said:**
> hi

what is the best program or method to download mp3 extracts from youtube to my pc

regards

ubuntu 10.10

[http://www.youtube-mp3.org/](http://www.youtube-mp3.org/)

---

### Post by TeoBigusGeekus on 2011-05-04
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread to grab the video.
Once you have it
```
ffmpeg -i /path/nameofvideo -acodec libmp3lame -ab 320k nameofsong.mp3
```
320k is hideous for a youtube video, so you can lower it if you want.

---

### Post by Zaney Zebra on 2011-05-04
I have used 

[http://www.mp3ify.com/index-original.html](http://www.mp3ify.com/index-original.html)

---

### Post by soulcat on 2011-05-04
cheers thanx for your answers....now sorted

---

### Post by lakerssuperman on 2011-05-04
If you have Chrome/Chromium you can use the following plugin:

[http://www.chromeextensions.org/utilities/chrome-youtube-downloader/](http://www.chromeextensions.org/utilities/chrome-youtube-downloader/)


It provides an option to download in .mp4, .flv and .mp3 and integrates directly into the Youtube page you are viewing.

---

### Post by peyre on 2011-05-04
I use a Firefox add-on called YouTube mp3 1.0.2.  It works great for me.

---

