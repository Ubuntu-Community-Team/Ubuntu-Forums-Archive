---
title: "OpenFiler or FreeNAS to rsunc ubuntu servers"
date: 2009-11-06
forum: General Help
---

### Post by Data-Base on 2009-11-06
Hello,

we are a school with a limited internet bandwidth

our students started to use Ubuntu more and more on their Computers :-)

so how I can make our Openfiler (we can use FreeNAS if it is easier) to use rsync and get the ISOs (and the updates) from Ubuntu Servers (like rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso)

so we can have an auto update with the latest ISOs

cheers

---

### Post by Giblet5 on 2009-11-06
I'm not sure that you can without hacking Openfiler. I presume that if you were capable of doing that, you would not ask how this could be done, so it's time to look at alternatives.

Any linux workstation or server using Openfiler's storage with write permission can simply run

```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/karmic-desktop-i386.iso PATHTOOPENFILERSTORAGEFOLDER
```

out of cron.

---

