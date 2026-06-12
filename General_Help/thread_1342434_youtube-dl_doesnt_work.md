---
title: "youtube-dl doesnt work??"
date: 2009-11-30
forum: General Help
---

### Post by gfunkera on 2009-11-30
i use youtube-dl to download stuff but lately the -b and -t options dont work, it wont download best quality and extract the title.. anyone got any ideas?

i use youtube-dl -bt [www.urlhere.com](www.urlhere.com) and it doesnt even download the flv.. when i use youtube-dl by itself, then it works...

---

### Post by PeEllAvaj on 2009-11-30
The best technique I have found is to use chromium-browser, and just load the video in the browser. When it is finished loading, you rename it and copy it out of /tmp/ to whatever you want.

Would that work for you?

---

### Post by gfunkera on 2009-11-30
i can definitely try that, although it is much less convenient because it means that i have to download another browser and not use the one i like to use (firefox)

im just curious as to why it would all of a sudden stop working....

---

### Post by andrew.46 on 2009-12-01
Hi gfunkera,

> **gfunkera said:**
> i use youtube-dl to download stuff but lately the -b and -t options dont work, it wont download best quality and extract the title.. anyone got any ideas?

The version in the repository is quite old. You can manually add a  newer version, which has been adjusted for recent youtube changes, as follows:

```
$ sudo apt-get remove youtube-dl
$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2009.09.13/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl
```

Hope this helps?

Andrew

---

### Post by Vaphell on 2009-12-01
i don't know what chrome would be for, if you watch some clip in firefox it is cached in /tmp too. Just load some and goto /tmp to see it's there, it's deleted as soon as you close the page (so don't do it until you copy it:)).

---

### Post by scouser73 on 2009-12-01
You can use this for downloading YouTube videos: [[COLOR="Red"]**YouTube Catcher**[/COLOR]]("http://www.youtubecatcher.com/")

---

