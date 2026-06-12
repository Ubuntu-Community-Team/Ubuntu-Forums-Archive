---
title: "how can i downgrade the graphic card driver?"
date: 2009-08-27
forum: General Help
---

### Post by chriskin on 2009-08-27
i was stupid enough to try the 185 drivers of nvidia on my 8600.  seems that my pc didn't love them, and all i can do is start in low graphics mode

how can i go back to the 180 ones?
they are not available through the "hardware drivers" menu

---

### Post by NoaHall on 2009-08-27
The way I did it (earlier today :D) was - uninstall EVERYTHING with nvidia 
Then do Ctrl + Alt + 3 and install it from there ~(185), it will come up with a few errors, but all will be fine :D It works great now.

---

### Post by bear24rw on 2009-08-27
I don't know if that will work but you can try purging your current one and installing a previous one
```

p   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
c   nvidia-glx-180                  - Transitional package for nvidia-glx-185   
i   nvidia-glx-185                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-71                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-96                   - NVIDIA binary Xorg driver      

```

---

### Post by chriskin on 2009-08-27
> **NoaHall said:**
> The way I did it (earlier today :D) was - uninstall EVERYTHING with nvidia 
Then do Ctrl + Alt + 3 and install it from there ~(185), it will come up with a few errors, but all will be fine :D It works great now.

i tried this and it seems to be working, (even though i did it in a more gui way, using envyng)

i haven't tested it with games and hd movies yet though
:popcorn:

edit : i REALLY missed the normal size icons of a regular resolution, how did we survive with so low resolutions in the past ?!?

---

### Post by NoaHall on 2009-08-27
It works great for me, my video is perfect! Much better than it was before.

---

