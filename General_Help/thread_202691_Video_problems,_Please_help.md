---
title: "Video problems, Please help"
date: 2006-06-23
forum: General Help
---

### Post by carguy0625 on 2006-06-23
I'm pretty new to linux.  I ran easyubuntu and I think I had it add the ATI drivers, now all my screensavers are horribly slow.  My card is an ATI radeon 9000 RV250.  I don't know what to do to get my video to work better. Any help is greatly appreciated.

---

### Post by xXx 0wn3d xXx on 2006-06-23
To find out if fglrx accel. is enabled do the following in terminal:
> fglrxinfo
This should not say Mesa if it does fglrx is not enabled.
> glxgears -printfps
You should get 500+ fps with this command.

Now how to fix it...follow [ this tutorial ](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue) to make it work.

---

### Post by carguy0625 on 2006-06-24
this is the out put of fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

and this is what I got with glxgears -printfps

973 frames in 5.2 seconds = 188.404 FPS
928 frames in 5.4 seconds = 172.182 FPS
892 frames in 5.4 seconds = 163.696 FPS
927 frames in 5.3 seconds = 174.889 FPS
904 frames in 5.6 seconds = 160.694 FPS

---

### Post by carguy0625 on 2006-06-24
I couldn't get that tutorial to work for me.  After I was done and tried to run fglrxinfo it gave me a long list of errors.

---

### Post by scxtt on 2006-06-24
try using either the "ati" or "radeon" drivers ... and try those 2 commands again ...
```
Section "Device"
        Identifier  "ATI Graphics Adapter"
        Driver      "ati"                      #or try radeon
        BusID       "PCI:1:0:0"
EndSection
```

---

### Post by Patrick-Ruff on 2006-06-24
I never take the easyubuntu route. it doesn't give me enough detail of what is *actually* going on. I forgot the link to the wiki tuturial, but it has always worked perfectly for me, you also have to remove fglrx from the linux-restricted-modules. (I forgot where the directory is however. someone else will know)

good luck

---

