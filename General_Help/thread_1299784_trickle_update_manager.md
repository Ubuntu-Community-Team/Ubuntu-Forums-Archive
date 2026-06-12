---
title: "trickle update manager"
date: 2009-10-24
forum: General Help
---

### Post by P4man on 2009-10-24
Im trying to throttle update manager so I can still browse and watch clips on my 1mbit connection while it downloads yet another 100Mb+ set of updates.

I installed trickle and tried this:

```
trickle -u 10 -d 20 update-manager
```

It gives no error, but the throtteling doesnt work either. It still donwloads at full speed.

I tried adding sudo in front, makes no difference.

Any ideas?

---

### Post by duanedesign on 2009-10-24
maybe try:

sudo apt-get update

sudo trickle -u 10 -d 20 apt-get upgrade

Note: make sure to look over the X:installed X:upgraded X:removed since you are on a development release (I am assuming by the update size you are running Karmic) apt-get upgrade wont throw up a dialog box warning you of a partial upgrade.

[Ubuntu Geek - bandwidth shapers]("http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html")

---

### Post by P4man on 2009-10-24
That actually works, thanks. Any idea why the other approach doesnt? Does trickle only throttle terminal apps and not graphical ones?

---

