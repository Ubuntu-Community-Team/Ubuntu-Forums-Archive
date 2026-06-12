---
title: "How to get temp using nvidia-settings?"
date: 2009-08-17
forum: General Help
---

### Post by Chrus on 2009-08-17
Playing around with my conky settings, trying to get my GPU temps to show. Ive got 2x GeForce 8800s running in SLi. I can get the temp for the gpu:0, but cant for the life of me work out how to get the temp of gpu:1.

Here's what ive got so far:
```
${color #1EFFFF}GPU Core Temp: $color${exec /usr/bin/nvidia-settings -q gpucoretemp |grep Attribute |cut -c 42-45}'C
```

Any ideas?

Cheers

---

### Post by Chrus on 2009-08-17
bump?

---

