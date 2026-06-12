---
title: "nvidia glxgears low suddenly"
date: 2010-02-21
forum: General Help
---

### Post by sigurnjak on 2010-02-21
I have been using nvidia 195 drivers for a while . Today out of curiosity i fired glxgears up and all i get is about 379 fps . I used to get 20000 + fps . I am using nvidia 7600 gs card . Does anyone have any ideas about hotw to find out what is wrong . Currently i am not  using compiz or anything fancy  and all video is fine , no jerkines or anything . I am just curious about drop in FPS number and how to troubleshoot it .

We all like big numbers !;)

---

### Post by Crafty Kisses on 2010-02-21
That's very strange. I would suggest changing the nVidia driver to an older version, just to see if that solves the issue. Another thing you can do is see if direct rendering is on, you  can run:
```
glxinfo | grep direct
```
That will tell you if direct rendering is on.

---

### Post by sigurnjak on 2010-02-21
Here is terminal output :
andrey@andrey-desktop:~$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 


I guess i am O.K. there .

Since i do not like messing with drivers out of fear of loosing my  x , what else i could do before trying different driver ?

---

### Post by Crafty Kisses on 2010-02-21
Here's something you should try, try moving the window where glxgears is running, and just see if the FPS goes up, and if not, let's see the results of the following:
```
dmesg
```

---

### Post by sigurnjak on 2010-02-21
Hi there Crafty Kisses ! Thank you very much for trying to help me . 
I have been looking at what kind of changes i did recently . 
Well , while back i tried some custom settings and  i  created custom file nvidia .rc and added it to startup and made executable . . It must have fixed what was bothering me  so i forgot about it . I just removed it  , rebooted and all is well .
I still do not remember why i had to that . :D

andrey@andrey-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
28591 frames in 5.0 seconds
29025 frames in 5.0 seconds
29021 frames in 5.0 seconds

All is well now !

---

### Post by Crafty Kisses on 2010-02-21
Yeah no problem! I'm so glad you got your problem fixed! Have a good day. :KS

---

