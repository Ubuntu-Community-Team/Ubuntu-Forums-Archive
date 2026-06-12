---
title: "Parole doesn't disable screen saver"
date: 2011-08-05
forum: General Help
---

### Post by floydian_slip on 2011-08-05
Hi,

Anyone else have this problem? I've checked the "Disable screen saver while playing movies" checkbox, but my screen still fades to blank after 10 minutes.

This doesn't happen in VLC, but VLC is giving another whole problem: [http://ubuntuforums.org/showthread.php?t=1817386](http://ubuntuforums.org/showthread.php?t=1817386).

Thanks.

Brian

---

### Post by Toz on 2011-08-05
Prior to starting your movie, try running (from the command line):
```
xset -dpms
```
to turn off the monitor energy star features. After the movie is done, re-enable them with:
```
xset +dpms
```

---

