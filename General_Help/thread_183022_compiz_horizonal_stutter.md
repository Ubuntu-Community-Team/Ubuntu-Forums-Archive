---
title: "compiz horizonal stutter"
date: 2006-05-27
forum: General Help
---

### Post by skippy81 on 2006-05-27
Hi, I have XGL and Compiz up and running really well, but if I drag a window from side to side it has a really horrible jerky look, as if its not moving in sync.  

If I move the same window up and down I get a really nice smooth motion.  

1m using a 6200 Geforce card, does anyone have any ideas?

---

### Post by testube_babies on 2006-05-27
Try opening gconf-editor and going to /apps/compiz/general/screen0/options and setting refresh_rate to 60.  I'm not sure it'll work, but it's worth a shot.

---

### Post by skippy81 on 2006-05-27
Im afriad it didnt work. I tried a whole range of values which I could and none of them made a big improvement.

I appear to have got the problem somewhat pinned down, its to do with the VSync of the nvidia drivers.   I used "export __GL_SYNC_TO_VBLANK=1" to fix the tearing effect when I move the cube around, but it seems to have no effect on the tearing as I move the windows from side to side. Strangely enough moving them up and down is fine.

---

### Post by mostwanted on 2006-05-27
Be sure to uncheck the auto-detect option BEFORE you set your refresh rate to 60.

---

### Post by skippy81 on 2006-05-27
Yeah I did that, it was definately affecting my refresh rate since when I put it too high I got problems, its now resting at 60 but I still have mucho stutter around the left and right window edges when I move windows horizontally.  

I used "export __GL_SYNC_TO_VBLANK=1" in my gdm init file in an attempt to sort the problem out since it seems to be a case of vsync tearing.  Doing this made a huge difference to 'the cube' now when I rotate it I dont get an ugly stuttering effect.  However when moving windows, the "export __GL_SYNC_TO_VBLANK=1" seems to have had no effect whatsoever.. ](*,) 

I think the issue is actually with my nvidia cards driver setup, since I actually tried not loading compiz and xgl and still got a less notable, but still present. tearing effect.  I am using the 8762 nvidia drivers.   

Please keep the ideas flooding in guys, and thanks for your responses so far:KS  ...

---

