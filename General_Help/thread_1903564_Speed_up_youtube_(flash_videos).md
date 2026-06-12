---
title: "Speed up youtube (flash videos)"
date: 2012-01-02
forum: General Help
---

### Post by The Little Book of Calm on 2012-01-02
Whilst I had windows xp on my laptop I also had AVG Flash Accelerator which helped my computer manage 720p videos (just). I was wondering if there was something similar avaible in the software center. Had a quick look but I didn't see anything , either that or I manage to overlook what I wanted.

Could you also recommend an add blocker to stop annoying flash ad's draining my cpu?

---

### Post by Paddy Landau on 2012-01-03
Sorry, I have not come across anything that can speed Flash. You don't say what version of Ubuntu you're using. If it's an old computer you have, you may want to consider using Lubuntu (for low-spec machines) instead of Ubuntu.

Regarding an ad-blocker, have a look at [Adblock Plus]("https://addons.mozilla.org/firefox/addon/adblock-plus/") (also available for Chromium).

---

### Post by pqwoerituytrueiwoq on 2012-01-03
you can pause the video and run it in the movie player with line if code from (terminal)
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```

---

### Post by Anstice on 2012-01-03
> **pqwoerituytrueiwoq said:**
> you can pause the video and run it in the movie player with line if code from (terminal)
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```

Just did this. Mind = blown.

---

### Post by claracc on 2012-01-04
> Originally Posted by pqwoerituytrueiwoq View Post
you can pause the video and run it in the movie player with line if code from (terminal)
Code:

d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"



I have tried this code in my lubuntu 11.04 laptop with this flash video from bbc news: [http://www.bbc.co.uk/news/world-asia-16402160](http://www.bbc.co.uk/news/world-asia-16402160) but I obtain "not found address", of course I have replaced totem by smplayer( no totem in lubuntu). Could you address me in order to obtain the right address for this embedded bbc video?

Thankyou very much in advance.

---

### Post by Maleificus on 2012-01-04
> **pqwoerituytrueiwoq said:**
> you can pause the video and run it in the movie player with line if code from (terminal)
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```

Wow, you just taught me something I will use on a regular basis, thanks!

---

### Post by Anstice on 2012-01-04
I get the same error when I run this using totem in Ubuntu so it's not a lubuntu thing. No idea why it's doing it though.

---

