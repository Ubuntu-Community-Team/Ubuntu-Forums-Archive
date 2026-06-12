---
title: "Quad-Core Conundrum"
date: 2009-08-03
forum: General Help
---

### Post by cj100570 on 2009-08-03
I'm running an Intel Q6600 oc'd to 3 GHz. For the most part I'm extremely happy with the performance of my machine. Recently I tried using gtk-recordMyDesktop to record me playing Unreal Tournament. Unfortunately my framerates went into the crapper and the game stuttered like crazy. I'm guessing that the game and gtk-recordMyDesktop were running on the same core. What I'd like to know is how can I have my system automatically load a program to a core with a small load?

---

### Post by MaxIBoy on 2009-08-03
I know you can set the processor affinity on an already-running process. However, if the affinity is not "pegged" in this way (to one or more specific processors/cores) the OS should automatically move processes around.

No, the reason your framerates are so bad is because most (all?) Linux screencapture programs aren't hardware-accelarated in anyway, dragging framerates down to worse-than-software-rendering levels. It's graphics-card accelerated when you render the frame, but it's not so accelerated when when the software pulls the frame off the framebuffer into main memory, doing the same for sound, then compresses the frame against a stored buffer of previous frames, before re-relinquishing control and allowing the graphics card to render the next frame. (Or something like that, the process varies and I'm no expert.) I mean, if you've ever done video editing, think of how long it takes to export the final product, which is probably a much lower screen resolution than you're running your game. Certainly longer than the length of the actual video. Acceptable if you're just showing off Compiz or something, but for gaming it's completely a unacceptable performance hit, doesn't matter how many cores you have (and throwing more cores at the problem might even make it worse.)

---

### Post by cj100570 on 2009-08-03
> **MaxIBoy said:**
> I know you can set the processor affinity on an already-running process. However, if the affinity is not "pegged" in this way (to one or more specific processors/cores) the OS should automatically move processes around.

No, the reason your framerates are so bad is because most (all?) Linux screencapture programs aren't hardware-accelarated in anyway, dragging framerates down to worse-than-software-rendering levels. Acceptable if you're just showing off Compiz or something, but for gaming it's completely a unacceptable performance hit, doesn't matter how many cores you have (and throwing more cores at the problem might even make it worse.)

Thanks for the response. It actually makes sense not that I think about it seeing as how even showing off compiz actually produces a slight bit of jumpiness too.

---

