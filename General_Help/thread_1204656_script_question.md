---
title: "script question"
date: 2009-07-05
forum: General Help
---

### Post by sr_guy on 2009-07-05
I'm writing a simple script to be able to dump a video stream to a file. It'll run daily. Using this script:

```

#!/bin/bash
cd /var/lib/mythtv/videos
mplayer-dumpstream -dumpfile "thaichan.mpg" "mms://58.147.79.139/Ch33333333333333333333"
/usr/share/mythtv/mythvideo/scripts/imdb.pl -M tv=no;video=no

```

How do I force the dumped filename to be changed slightly using the current system year/day/month inside the filename, so that the file isn't overwritten each day?

i.e. 
Day 1  = thaichan20090407.mpg
Day 2 = thaichan20090507.mpg
Day 3 = thaichan20090607.mpg

Ect...

---

### Post by andrew.46 on 2009-07-05
Hi sr_guy,

> **sr_guy said:**
> 

```
mplayer-dumpstream -dumpfile "thaichan.mpg" 
```

How do I force the dumped filename to be changed slightly using the current system year/day/month inside the filename, so that the file isn't overwritten each day?

i.e. 
Day 1  = thaichan20090407.mpg
Day 2 = thaichan20090507.mpg
Day 3 = thaichan20090607.mpg

You could try the following:

```
mplayer-dumpstream -dumpfile thaichan`date +%Y%d%m`.mpg 
```

Note the backticks: ``.

All the best,

Andrew

---

### Post by sr_guy on 2009-07-05
andrew.46, that worked great, thanks! While I'm at it there is one last thing that I need with this script.

I need the video file to be forced to a particular resolution. At a full 720x480 resolution on a tv screen is a bit grainy. I'm thinking more like 400x300 to keep it a little cleaner.

I tried:

```

mplayer-dumpstream -dumpfile thaichan`date +%Y%d%m`.mpg -geometry 400x300 "mms://58.147.79.139/Ch33333333333333333333"

```

but that did not do the trick. Any other help would be appreciated.

---

### Post by andrew.46 on 2009-07-06
Hi sr_guy,

> **sr_guy said:**
> 
I need the video file to be forced to a particular resolution. At a full 720x480 resolution on a tv screen is a bit grainy. I'm thinking more like 400x300 to keep it a little cleaner.

I tried:

```

mplayer-dumpstream -dumpfile thaichan`date +%Y%d%m`.mpg -geometry 400x300 "mms://58.147.79.139/Ch33333333333333333333"

```

Not sure I can help with that one, although the geometry option is not the one you are after as it has more to do with position on the screen than resizing. I downloaded a little of that stream and I believe its native resolution is actually 320x240, and I am a little unsure as to how you can force a device like a television to respect this setting. Hopefully somebody else has an idea?

All the best,

Andrew

---

