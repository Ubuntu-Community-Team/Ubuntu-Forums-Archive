---
title: "performance and vsync"
date: 2012-01-17
forum: General Help
---

### Post by Cnaeus on 2012-01-17
Hi,
I just installed bodhi 1.3, got the latest nvidia driver - yet I still experience some performace issues, as well as vertical tearing in videos :(
I have an HP presario CQ61 with 2.1 Ghz dualcore processor and nVidia 103m video card (512 Mb) and 3 Gigs of RAM.
I guess programs like Stellarium (simple star obervatory 3d app) should not lag and vertically tear on my machine. Also, the lack of vsync is also quite annoying when watching videos - especially youtube.
Is there anything to do about it?
Thanks

---

### Post by Cnaeus on 2012-01-20
Um, I intended this post for the BodhiLinux forums, it ended up here because of some very stupid mistake...
Anyway, I found out that by disabling fullsceen compositing, (composite->memory->don't composite fullscreen) the fullscreen 3d apps performance improved a lot. As for the vsync, swiching the driver from software to opengl helped a bit.

---

