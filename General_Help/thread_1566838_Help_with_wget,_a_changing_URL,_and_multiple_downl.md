---
title: "Help with wget, a changing URL, and multiple download links"
date: 2010-09-02
forum: General Help
---

### Post by redfox1160 on 2010-09-02
Hello!

This is very similar to a previous post of mine. I have no clue how to go about doing this though. If someone could give a little explanation of what the script is actually doing I would appreciate it.

I want to download videos from a website in this format:
[B]
[COLOR="Black"]http://twit.cachefly.net/video/floss/floss0133/floss0133_xvid_320x240_500.mp4[/COLOR][/B]

The parts in red change each week when a new episode comes out. Here are two weeks links:

[B][COLOR="Black"]http://twit.cachefly.net/video/floss/floss[/COLOR][COLOR="Red"]0133[/COLOR]/floss[COLOR="Red"]0133[/COLOR]_h264b_864x480_1000.mp4

[COLOR="Black"]http://twit.cachefly.net/video/floss/floss[/COLOR][COLOR="Red"]0132[/COLOR]/floss[COLOR="Red"]0132[/COLOR]_h264b_864x480_1000.mp4[/B]

Does anyone know how I can use wget to download from each weeks link automatically? I know i can make a crontab and schedule it, but I don't know how to do it when the URL changes each week. Also, this is the link where I can get the download links from: **[COLOR="Black"]http://feeds.twit.tv/floss_video_large[/COLOR]**.

The last time I asked a very similar question, and this is the script that [DaithiF]("http://ubuntuforums.org/member.php?u=867532") wrote most of:
```
#!/bin/bash
wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > /home/eric/media/videos/lasttekzilla.txt && wget -O /home/eric/media/videos/tekzilla.wmv $(cat /home/eric/media/videos/lasttekzilla.txt) && chmod 777 /home/eric/media/videos/tekzilla.wmv

```

I added some things to it, but the hard stuff was done by DaithiF. I don't know if this script would help or not. Thanks!

---

