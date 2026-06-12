---
title: "X server error[no gui]"
date: 2009-12-20
forum: General Help
---

### Post by aninona on 2009-12-20
Just installed karmic 64 bit and when booting getting CLI.
trying to run startx outputs:
```
xinit: no such file or directory (errno 2): unable to connect to X server 

```

I understood it is something with the screen driver but I have no idea how to fix it.

Thanks.:P

---

### Post by NoaHall on 2009-12-20
Run these - ```
locate xinit
``````
locate gdm
```

---

### Post by aninona on 2009-12-20
> **NoaHall said:**
> Run these - ```
locate xinit
``````
locate gdm
```

tried it got many lines. then run starx again and got the same error+I realized that it says somewhere
(EE) failed to load module nvidia(module does not exist, o)
(EE) no drivers available

---

### Post by NoaHall on 2009-12-20
Ah. I can't help you exactly right now, as I'm not home - so I can't remember the name of the nvidia packages. Try running ```
apt-cache search NVIDIA
apt-cache search nvidia
```

---

### Post by aninona on 2009-12-20
Ran it and got many lines. What should I do with it?
Haven't solved it yet.

---

