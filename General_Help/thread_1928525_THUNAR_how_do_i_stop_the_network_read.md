---
title: "THUNAR: how do i stop the network read"
date: 2012-02-20
forum: General Help
---

### Post by godsgifttoearth on 2012-02-20
how do i stop the stupid network function on thunar that causes it to lag for a good 20seconds on first start up?

---

### Post by Toz on 2012-02-20
What version of xfce and (x)ubuntu are you using? I'm using Xubuntu 11.10 and I don't experience this delay (and yes, I do have gvfs-backends installed).

As a workaround, you can try editing /usr/share/gvfs/mounts/network.mount and changing:
> AutoMount=true
...to
```
AutoMount=false
```
This will move the delay to when you click on the Network link in Thunar, but Thunar should start up right away.

---

