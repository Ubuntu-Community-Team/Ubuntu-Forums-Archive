---
title: "Whoa! What was that?"
date: 2012-05-04
forum: General Help
---

### Post by Lloydb39 on 2012-05-04
I shut down my computer and put in a new clock battery because it kept losing time. Booted back up to Ubuntu 11.10 and got no display. Finally hit alt-ctl-del and got a screen offering normal boot, or recovery. I chose recovery and it did something, apparently creating a new swap area in a partition, and then rebooted. Everything seems to be normal now. Whew! I have no clue what I could have done to bring that on. Anyone?

---

### Post by Habitual on 2012-05-04
```
grep "it did something" /var/log/*
```

---

### Post by lindsay7 on 2012-05-04
Putting in the new battery reset the bios to the factory settings for the motherboard. That could have messed things up.

---

