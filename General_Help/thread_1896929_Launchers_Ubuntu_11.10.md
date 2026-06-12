---
title: "Launchers Ubuntu 11.10"
date: 2011-12-18
forum: General Help
---

### Post by Super-Dan on 2011-12-18
Hi there

I have Ubuntu 11.10 set up for my mum in Gnome classic.

I need to make a Launcher mainly for:

Nautilus
Freeze - Bubble 2 (a game I downloaded for free)
Internet
Settings

Can you help me?

I know...

gnome-desktop-item-edit ~/Desktop/ --create-new

But how do I then go onto creating a Launcher for each individual program?

---

### Post by lechien73 on 2011-12-18
Do you mean that you want a classic desktop launcher? Are you looking for the filenames? Sorry if I've misunderstood the question :)

---

### Post by satanselbow on 2011-12-18
Launchers for all your installed apps can be found in /usr/share/applications so you can just copy them from there as root to your ~/Desktop folder ie:

```
gksu nautilus /usr/share/applications
```

---

