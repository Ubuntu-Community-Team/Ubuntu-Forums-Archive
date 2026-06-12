---
title: "Graphics drivers VESA: SUMO"
date: 2012-06-02
forum: General Help
---

### Post by GuitarHero on 2012-06-02
I just bought the humble bundle and tried to play Limbo but it was very choppy.  I have a lenovo ideapad with a radeon dedicated graphics card.  I am able to play much more graphically demanding games on my windows partition.  I have the additional driver set to ATI/AMD proprietary  fglrx graphics driver.  When I go to system - details it says driver: VESA: SUMO for graphics.  Is it using the right driver?  It seems like it should run the game smoothly.

Thanks!

---

### Post by Mark Phelps on 2012-06-03
IF you mean system info, that is known to be unreliable in what it reports.

It looks like you may have the open-source driver installed.

To find out, open an terminal and enter "fglrxinfo".  IF it says not found, you don't have the AMD restricted drivers (fglrx) installed.

---

### Post by GuitarHero on 2012-06-10
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon 6600M and 6700M Series
OpenGL version string: 4.2.11627 Compatibility Profile Context


Psychonauts wont even open.  Limbo runs extremely slowly.

---

