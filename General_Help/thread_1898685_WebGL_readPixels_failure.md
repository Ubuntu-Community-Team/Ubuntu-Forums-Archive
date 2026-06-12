---
title: "WebGL readPixels failure"
date: 2011-12-21
forum: General Help
---

### Post by Bruce Sherwood on 2011-12-21
Ubuntu 11.10 on desktop and laptop 386 machines, both with NVIDIA cards, using the recommended NVIDIA proprietary driver: WebGL readPixels seems to fail with both Firefox and Chrome. I've implemented a standard mouse-picking algorithm, which is to render on a hidden canvas with no lighting and with each object having a false color equal to its ID. The canvas is scissored (clipped) to the one pixel under the mouse, and readPixels gets the color of that pixel, which yields the ID of the object. This works fine on all WebGL-enabled browsers on Windows and Mac, but on Ubuntu I always get the background color to which the canvas was cleared at the start of the render. 

I've tried many many different tests including setting preserveDrawingBuffer to true (should be irrelevant as readPixels is executed before exiting the render routine), trying to read from the regular canvas the color of the pixel under the mouse (in which case there is no scissoring), etc. In no case do I ever manage to see a color other than the background color. I'd appreciate hearing from a developer who has made WebGL readPixels work properly. Thanks.

---

