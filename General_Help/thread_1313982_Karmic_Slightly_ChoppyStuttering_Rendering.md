---
title: "Karmic: Slightly Choppy/Stuttering Rendering"
date: 2009-11-04
forum: General Help
---

### Post by COW-tz on 2009-11-04
On my fresh Karmic Install I have an issue with 2D/3D rendering:

It is most apparent when playing Quakelive: While I have a very constant 125fps, it still looks as if I was playing with 10-20fps.
There is this constant stuttering. It's not a CPU load surge or anything like that, the stuttering is very uniform and always feels the same.

It's also apparent when moving around Windows on the Desktop or sometimes when watching video (even with mplayer and vdpau support) where a linear motion is stuttering with what looks like just about the same frequency as in the Quakelive example above.

So I'm using an 8-Series Nvidia graphics card. I've tried different drivers, changing sync to blank settings, but there's no change in stuttering at all.

In Jaunty everything works just fine though (with the same nvidia drivers)

I can't find any strange processes that would cause CPU load.

Generally, everything's running quite smoothly, though there's that underlying slight stuttering to everything rendered on the screen. It isn't disturbing or very noticeable when working or watching video, it makes it impossible to play Quakelive though.

I have no clue what could be wrong here...

---

### Post by Chryseus on 2009-11-04
I have the exact same problem.
I have no idea what is the cause though.
Could you post your hardware specs please.

---

### Post by elma_illusion on 2009-11-04
I am having the same problems here on mij Asrock ION330. 

I've tried the 18x and 190 driver from NVIDIA but the results are the same. Ubuntu states that the drivers are installed correctly and it is possible to view video using the GPU.

---

### Post by elma_illusion on 2009-11-07
I have fixed the problem within an application. It has something to do with de VerticalSync setting somewhere.

---

### Post by COW-tz on 2009-11-07
Ok, it is an issue with compiz:

When disabling Visual Effects completely, the stuttering stops.
But I see some pretty nasty Vsync artifacts when moving around windows on the Desktop. I tried messing around with the compiz settings in gconf-editor, but that won't change anything.

Changing the Sync to VBlank setting in Nvidia X Server Settings tool has no effect either.

At least I can play Quakelive now, of course I haven't enabled Sync to VBlank for OpenGL in the Nvidia X Server Settings tool.

---

