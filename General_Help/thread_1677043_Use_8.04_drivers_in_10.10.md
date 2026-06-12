---
title: "Use 8.04 drivers in 10.10"
date: 2011-01-28
forum: General Help
---

### Post by Heartless Angel on 2011-01-28
im using 10.10 right now, only it has no video drivers compatible with my graphics chip. 8.04 had such drivers, but i dont know how to install them in 10.10

please tell me how

---

### Post by coffeecat on 2011-01-28
If you installed the 8.04 graphics driver in 10.10 it would not be compatible with the newer version of xserver in 10.10 and you would probably precipitate a failure of the xserver. What graphics chipset do you have?

---

### Post by Heartless Angel on 2011-01-28
nothing fancy, just an on board intel 82845g graphics controller

its  pretty old, but like i said, it can still run basic desktop effects ans so forth

thanks!!

---

### Post by coffeecat on 2011-01-28
I had a feeling it might be the Intel 8** series graphics. Not particularly good news, but you might find this useful:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

It tells you how to enable the vesa driver for different resolutions or the Intel driver for 3d, but the price you pay for the latter is instability.

---

### Post by Heartless Angel on 2011-01-28
merrrrrrr
ok, well that doesnt really seem like its worth it, although i really want it to have proper drivers for the video........ i think i'll just switch back to 8.04 and just use the themes and things that come with 10.10 after i get it all set up. thanks for the help though, i think 10.10 would be better used on a newer computer, not my old clunker, lol

---

