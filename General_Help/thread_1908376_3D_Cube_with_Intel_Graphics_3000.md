---
title: "3D Cube with Intel Graphics 3000?"
date: 2012-01-13
forum: General Help
---

### Post by Rag888 on 2012-01-13
Do the Intel Graphics 3000 card support 3D, and can i have the 3D Cube effects on my Ubuntu with this card?

i have install Compiz and activated the 3D Cube and 3D Cube Rotate, also the wobbly windows etc, but my desktop, though it can be rotated, but its in 2D, i mean not in the shape of a Cube rather it's just like fliping a paper.

Why?

---

### Post by kevdog on 2012-01-13
Your driver loaded and running for that card is probably not correct.  You are going to have to do an internet search and see what linux driver is appropriate for your graphics chipset.

Also if you could list the following:
lspcii -nn | grep VGA
lshw -C display

Thanks.

---

### Post by LewisTM on 2012-01-13
Go to the Compiz Config Manager/General Options/Desktop Size and set the horizontal virtual size to 4 and the rest to 1.
You can also achieve other geometric shapes with different numbers but since you cannot get a 3D object with only two faces, you get a flipping page...

Cheers!

---

### Post by Rag888 on 2012-01-13
Intel Graphic Card 3000 is the only VGA Card whose driver is inbuilt in  Ubuntu. Whereas even for Nvidia one has to do the 'special driver  install' thing, but not with intel.

Anywaz, i find out the way from another site as Lewis pointed out that i had to do it with the "gen setting' option. i just changed the the range of horizontal setting to 4 and it is working now. So thankyou.

And how to get 'other' shapes? i can see cylindrical shapes of desktops on the net?

---

### Post by LewisTM on 2012-01-13
Ahh the cylinder. It's in Cube Reflection and Deformation.
Have fun!

---

