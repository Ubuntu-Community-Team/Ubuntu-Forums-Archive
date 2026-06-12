---
title: "(Ubuntu 12.04) Watching streaming videos online makes computer hot"
date: 2012-06-05
forum: General Help
---

### Post by pretty_whistle on 2012-06-05
Should this be happening?  Is this normal? ( Firefox weighs in at 44% CPU. )

That's questions number 1 and 2.  The 3rd is:  What can I do about it?

---

### Post by pretty_whistle on 2012-06-05
Anyone?

---

### Post by traditionalist on 2012-06-05
If it is running too hot then you need to cool it.  If it gets too hot it will shut down. Quite a few machines are not powerful enough for some tasks and will overheat.  Make sure all cooling vents are clear and that fans are working.

You need to give some information about your machine if you want any sensible specific advice.

---

### Post by pqwoerituytrueiwoq on 2012-06-05
you can try underclocking by using jupiter (google it)
depending on the hardware/video source this can make a difference
pause the video
open a terminal (you will need [smplayer](apt:smplayer) installed)
```
cd /tmp;d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";smplayer -fullscreen /tmp/"movie-$d"
```

---

### Post by vasa1 on 2012-06-05
> **pretty_whistle said:**
> ... Is this normal? ( Firefox weighs in at 44% CPU. )
...
Give or take a little, I feel it's normal.

---

