---
title: "How to reinstall gfx drivers when using a new graphic card?"
date: 2010-08-23
forum: General Help
---

### Post by TheForumTroll on 2010-08-23
Can someone tell me how i clean out the old graphic drivers and install some new ones? I need a solution for two PC's: One where I'm swapping an ATI card with a newer ATI card and one where I'm swapping an ATI card with a new Nvidia card.

Just reinstalling/installing drivers does not work. I got no hardware acceleration and no title bars on the windows.

---

### Post by ajgreeny on 2010-08-23
If you were using the open source drivers that come when you install ubuntu, and not the proprietary drivers from System->Administration->Hardware Drivers all you should need to do is reboot after replacing the gfx card and let ubuntu detect the new card, then go to System->Administration->Hardware Drivers and see if there is a new proprietary driver available.

If you already had a driver working from the System->Administration->Hardware Drivers you will have to disable or remove it before you reboot, and also rename the /etc/X11/xorg.conf file that it produced with ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-bak
``` That should give you a clean start for the system to detect the new card.

More detail about the exact cards and drivers we are dealing with would have helped, but the above is a good start for you and may be all that is needed.

---

### Post by TheForumTroll on 2010-08-24
Thank you for your reply. Unfortunately it did not work. I still have no hardware acceleration or window title bars.

System->Administration->Hardware Drivers says "Nvidia_current" and that the driver is activated but not in use at the moment.

It is a Nvidia GTX 460 ("Gainward GTX 460 Golden sample Goes Like Hell" to be specific) and the old card I removed was an ATI Radeon HD 4850.

On the other PC i removed an ATI Radeon 4370 and inserted the 4850. It got the same problems.

---

### Post by realzippy on 2010-08-24
run

```
sudo nvidia-xconfig
```

and restart X or reboot.
Any difference?

---

### Post by TheForumTroll on 2010-08-24
No difference. It still says the driver is activated but not in use.

Xconf says:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```

---

### Post by realzippy on 2010-08-24
NVIDIA driver activated but not currently in use in ubuntu 10.04:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Common%20Issues](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Common%20Issues)

maybe this helps.

---

### Post by TheForumTroll on 2010-08-24
Thank you for the link. No luck though. Still says not in use.

---

### Post by realzippy on 2010-08-24
So let's have a look at the nvidia error log file.

Open a terminal:
```
sudo nvidia-bug-report.sh

```
creates a error log file in your home directory,can you post this ?

---

### Post by TheForumTroll on 2010-08-25
Sure. It is way too long to post though so I have [uploaded it in txt format here instead]("http://tweaks.dk/nvidia-bug-report.txt").

---

### Post by realzippy on 2010-08-25
Can't find anything "bad" in the log file.
Btw,if I right-click on Desktop/Visual effects,there is no checkbox marked although
compiz runs fine.If I "enable" it there,all compiz settings got smashed;use CCSM to enable visual effects.
What does

```
compiz --replace
```

and

```
glxinfo | grep direct
```


"say"?

---

### Post by TheForumTroll on 2010-08-27
compiz --replace fixes the missing titlebars until reboot.


glxinfo | grep direct says:
```
 
direct rendering: Yes
    GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 

```

---

### Post by realzippy on 2010-08-27
*"driver is activated but not in use."*

seems to be a bug.Your driver/direct rendering works;I have to admit that I do not know what "GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect" means.Little googling shows [this]("http://www.opengl.org/registry/specs/ARB/draw_indirect.txt") Seems to be a nvidia-feature,needs openGL 3.1...output on my machine:
```
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 

``` 
(I only run a GTX 260)

So your hardware acceleration seems to work.Further test :

```
glxgears
```

how many frames ?


Also:
```
nvidia-settings
```

only starts when the nvidia driver works.
BTW,the missing window-borders is also a bug ;it should disappear
when you enable auto-login for your users or simply
put *compiz --replace* in the autostart.
It is not exactly a compiz problem since the window-borders are made by compiz-decorator which starts when compiz starts(default settings).If you ran emerald window decorator (which I like more) it would be [I]emerald --replace

[/I]...

---

### Post by TheForumTroll on 2010-08-28
glxgears doesn't run with a lot of frames since vsync is enabled somewhere. It does seem to work though, as long as I use compiz --replace at login.

---

