---
title: "How to use git?"
date: 2010-02-10
forum: General Help
---

### Post by cd-r80 on 2010-02-10
How to use git? I want to download git://git.xfce.org/panel-plugins/xfce4-generic-slider. All what I get is:

~$ git clone [http://git.xfce.org/git/panel-plugins/xfce4-generic-slider](http://git.xfce.org/git/panel-plugins/xfce4-generic-slider)
Initialized empty Git repository in /home/john/xfce4-generic-slider/.git/
fatal: [http://git.xfce.org/git/panel-plugins/xfce4-generic-slider/info/refs](http://git.xfce.org/git/panel-plugins/xfce4-generic-slider/info/refs) not found: did you run git update-server-info on the server?

---

### Post by mc4man on 2010-02-10
I don't think there's anything you can do about that - your comm. is fine.

I don't use xfce so can't comment on plugin, but this should get you the latest snapshot ( noting there was only the initial commit and one update for a xml module

```
wget http://git.xfce.org/panel-plugins/xfce4-generic-slider/snapshot/xfce4-generic-slider-267d5ead4a928d536ea6c76ec0b1f4bcfc77f1f6.tar.bz2
```

you may want to read the few [comments here ]("http://goodies.xfce.org/projects/panel-plugins/xfce4-generic-slider")(if not already

---

### Post by cd-r80 on 2010-02-10
Ok. I could not compile it yet.

---

