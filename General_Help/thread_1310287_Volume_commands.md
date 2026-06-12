---
title: "Volume commands"
date: 2009-11-01
forum: General Help
---

### Post by Monotoko on 2009-11-01
Hiya :)

I have an alarm system in cron which plays a sound when i tell it to, but i need to play it at a certain volume.

I have searched google but cannot seem to find what i am looking for.

What i need is a command to set the master volume on my computer to 60% (from mute, or 10% or whatever)

any ideas what i could use?

Thank you :)

---

### Post by P4man on 2009-11-01
```
man amixer
```
should do the trick

---

### Post by Monotoko on 2009-11-01
Thank you, that works perfectly, the code i have used is:

```
amixer set Master 60%
```

for any future referance

---

### Post by Monotoko on 2009-11-01
How would i go about unmuting the volume? That only works if the volume is already unmuted

~Monotoko

---

### Post by Monotoko on 2009-11-01
bump

---

### Post by Kokopelli on 2009-11-01
"man amixer" tells me 

> The  parameters cap, nocap, mute, unmute, toggle are used to change capture (recording) and muting for the group specified.


so 
```

amixer set Master unmute

```

---

### Post by Monotoko on 2009-11-01
I have tried that, was one of the first things i tried, but it doesnt work :S

---

