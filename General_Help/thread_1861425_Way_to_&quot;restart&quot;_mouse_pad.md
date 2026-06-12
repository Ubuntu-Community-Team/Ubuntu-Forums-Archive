---
title: "Way to &quot;restart&quot; mouse pad?"
date: 2011-10-15
forum: General Help
---

### Post by Algus on 2011-10-15
I've had this odd bug crop up a time or two where my mouse pad seems to completely die on me.  It mainly seems to happen in Banshee when I'm trying to use the online features.

Basically the trackpad on my laptop stops working completely and I've had to log off and back on to get it working again.  Crossing my fingers that it is a bug that will be fixed for me but is there a terminal command or something I can use to "restart" my trackpad so I don't have to end my session anymore?

---

### Post by mc4man on 2011-10-15
this can many times restore - if it happens open a terminal (ctrl+alt+t
```
synclient TouchpadOff=0
```

I've been seeing this for a couple of weeks - you can try turning off the 'disable touchpad while typing' option in System settings > touchpad & mouse > touchpad

It's not guaranteed this will prevent, has here during 2 separate test periods of 3-4 days

If you need that option there is another way to enable that may also help prevent the random freeze up
(if in fact this is the cause..

---

### Post by davbran on 2011-12-16
> **mc4man said:**
> this can many times restore - if it happens open a terminal (ctrl+alt+t
```
synclient TouchpadOff=0
```

I've been seeing this for a couple of weeks - you can try turning off the 'disable touchpad while typing' option in System settings > touchpad & mouse > touchpad

It's not guaranteed this will prevent, has here during 2 separate test periods of 3-4 days

If you need that option there is another way to enable that may also help prevent the random freeze up
(if in fact this is the cause..

mc4man,

You're a god among men!!! I found this fix through my HTC Sensation. Instant fix.

db

---

### Post by whyDerrick on 2012-01-11
Since this is still open, I'd like to offer up thanks for that fix too.

---

