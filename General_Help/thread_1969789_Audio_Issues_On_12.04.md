---
title: "Audio Issues On 12.04"
date: 2012-04-30
forum: General Help
---

### Post by Kodeine on 2012-04-30
Salutations!

So after doing a fresh install of pangolin the volume indicator in the top left always shows mute (the volume icon and then three little lines (-) next to it). When clicking it and viewing the volume slider it's all the way to the bottom. Although I can still hear all sounds that Ubuntu makes via my monitor's speakers and from my headphones. Only problem is that I can adjust the volume as I said above.

Anyone know what the prob might be?

---

### Post by Enigmapond on 2012-04-30
Install gnome-alsamixer and it will give a small GUI to check all balances. You might also delete the file ~/.pulse. It's in your home folder...hidden. It will just redo itself with default parameters.

---

### Post by uylug on 2012-04-30
Try alsamixer, it's a console based tool to adjust volume levels.

```
alsamixer
```

---

### Post by Kodeine on 2012-04-30
> **Enigmapond said:**
> Install gnome-alsamixer and it will give a small GUI to check all balances. You might also delete the file ~/.pulse. It's in your home folder...hidden. It will just redo itself with default parameters.

Ah removing the pulse folder worked fine. Thanks!

---

