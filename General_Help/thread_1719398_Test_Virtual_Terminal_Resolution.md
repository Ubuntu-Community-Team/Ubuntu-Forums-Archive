---
title: "Test Virtual Terminal Resolution?"
date: 2011-04-01
forum: General Help
---

### Post by Jose Catre-Vandis on 2011-04-01
Searched everywhere for this, a multitude of threads and posts on how to change the resolution of a VT, but nothing on how to find out what it is?

So what is it?

```
run_some_command
```outputs (for example)```
1280x1024
```

---

### Post by Jose Catre-Vandis on 2011-04-04
As usual found / remembered (!) the answer:
```
fbset
```
gives
```
mode "1920x1080"
    geometry 1920 1080 1920 1080 32
    timings 0 0 0 0 0 0 0
    rgba 8/16,8/8,8/0,0/0
endmode
```

---

