---
title: "What to install for NVIDIA OpenGL/OpenCL/Cuda development?"
date: 2010-12-15
forum: General Help
---

### Post by outofsync on 2010-12-15
My card is NVIDIA (9600MGT) so I guess it's better to install NVIDIA headers rather than Mesa ones.

However, I installed nvidia-current-dev, and OpenGL headers go into /usr/include/nvidia-current/GL, which is a bit odd location (and not found by default by the compiler)

So... what should I do? create symbolic links manually so that I have /usr/include/GL? Or should I install Mesa headers? What's the recommended approach?

Thanks!

---

### Post by outofsync on 2010-12-26
I think something is broken in the approach for installing the OpenGL headers. For example, if I'm on nvidia hardware, and if I install the nvidia development packages, I expect the OpenGL headers to be on /usr/include/GL, and not on /usr/include/nvidia-current/GL.

Then there's another problem. The nvidia-current development package doesn't have a "glu.h" header. Searching on Internet, everybody says "install libglu1-mesa-dev". Ok, that would be fine if... libglu1-mesa-dev wouldn't depend on libgl1-mesa-dev and mesa-common-dev, which install the mesa OpenGL headers on /usr/include/GL.

So, it seems the only solution is to install the mesa development packages even if you don't use mesa. As I said, this approach looks broken.

---

### Post by outofsync on 2010-12-26
Finally I "fixed" it by downloading the Mesa-3.7 source code tarball, and manually copying the "glu.h" file to /usr/include/nvidia-current/GL

Sure, a very dirty solution, but I don't want to have mesa packages on my system (it's not anything personal against mesa, it's just that I don't want to have two sets of headers at the same time).

Also, I need to add -I/usr/include/nvidia-current to gcc when compiling, but I can live with that.

---

