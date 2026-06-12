---
title: "i just instaled ubuntu 9.04 on my desktop"
date: 2009-08-29
forum: General Help
---

### Post by ilych_ulyanov on 2009-08-29
it installed no problem and at first ran great. as soon as  i installed the proprietary drivers for my ati gpu through the hardware drivers app and rebooted the computer began to lag really really badly and now that i disabled them again it is back to normal. 
how can i get the drivers working with out the unbearable lag?
thanks for any help you can give me :)

---

### Post by GSF1200S on 2009-08-29
> **ilych_ulyanov said:**
> it installed no problem and at first ran great. as soon as  i installed the proprietary drivers for my ati gpu through the hardware drivers app and rebooted the computer began to lag really really badly and now that i disabled them again it is back to normal. 
how can i get the drivers working with out the unbearable lag?
thanks for any help you can give me :)

Can you find out what particular driver you are using? Ubuntu checks to see if your computer is capable of running compiz (has 3d acceleration capabilities), and if it does it of course enables them. If these drivers are poor, or your video card is poor, it will not be a smooth experience.

So, first, what ATI card do you have? This is important for us to know. We need to figure out whether you are using fglrx or whatever.

Gahh.. ill try to help you but all my computers have Nvidia cards, so we may need to wait for an ATI guru..

---

### Post by ilych_ulyanov on 2009-08-29
oh sorry forgot to add that i had a hd 4870
the thing i was trying to enable was "ati/amd proprietary fglrx graphics drivers"

---

### Post by ilych_ulyanov on 2009-08-30
bump

---

### Post by GSF1200S on 2009-08-30
> **ilych_ulyanov said:**
> oh sorry forgot to add that i had a hd 4870
the thing i was trying to enable was "ati/amd proprietary fglrx graphics drivers"

Well, you can disable compiz to start. Should be in System-> Preferences-> Appearence. Turn off all desktop affects, and enable the driver that Ubuntu suggests you enable. It will probably have you restart, at which point open a terminal and type the following command and paste the results here:

```
glxinfo
```

You can also run glxgears in the terminal and tell me what your FPS is. While this is not a good FPS benchmark, it does tell us the state of your 3d acceleration.

Also, please post the contents of the following file:

/etc/X11/xorg.conf

assuming its there now. I know X went configless not too long ago, but since im currently using Arch im not sure whether or not 9.04 is in the same boat.

---

