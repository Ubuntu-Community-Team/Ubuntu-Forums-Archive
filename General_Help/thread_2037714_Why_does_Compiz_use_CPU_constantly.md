---
title: "Why does Compiz use CPU constantly?"
date: 2012-08-05
forum: General Help
---

### Post by TheNessus on 2012-08-05
Look at this screenshot:
Compiz takes 8% CPU usage ALL THE TIME. sometimes it jumps to 12% and reverts back to 8%.

I have an i3 first gen processor with integrated graphics. (GMA something)

this is the same as with a vanilla install. system is 12.04 x64 always updated.

why is this happening? it's not like I move windows around all the time and using all the effects every second.

---

### Post by SoulTechnologist on 2012-08-05
I am not an expert about Compiz, but what I suppose is that it takes that much of CPU in order not to crash with low or older processors. One of my colleague had severe warming issues while using it, so that is my guess. But, as I pointed out, it is just a guess. There are of course more expert users here that could give you a more precise answer.

---

### Post by Frogs Hair on 2012-08-05
Compiz is the Window manager for Unity 3D but 8% seems high if constant. You could select Unity 2D at login and see if there is a difference. If you want to view top processes from the terminal use the following.```
top
```

With Chrome open in Unity 3D I'm at 3 to 6% CPU use and that is because Chrome is a bit of pig. I'm usually 0 and 3% with another browser open.

---

### Post by gifford on 2012-08-05
8% seems a bit high. Try disabling some of compiz settings using compizconfig settings manager. For some reason disabling all of image loading lessened my load.

---

