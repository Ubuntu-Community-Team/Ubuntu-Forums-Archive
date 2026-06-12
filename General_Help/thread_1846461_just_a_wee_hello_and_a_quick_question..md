---
title: "just a wee hello and a quick question."
date: 2011-09-19
forum: General Help
---

### Post by easily.confused on 2011-09-19
Hello all you good people. I've just installed ubuntu and have, what appears to be, the common problem with the nvidia drivers. As my name suggests I don't really get it a lot of the time, lol,  but I was wondering if un installing this version and then re installing an earlier version would solve the problem until a new release or update/bug fix comes around? 
Thanx for any responses. :P

---

### Post by uncontrolable™ on 2011-09-19
Which version are you trying to use and what are your hardware specifications?

---

### Post by easily.confused on 2011-09-19
The version I'm using is the latest one err 11.04? and the hardware I'm having trouble with is my GeForce 7050/nForce 610i graphics card. Is that enough info? sorry I'm not very sure about what the other hardware specs are.

---

### Post by Elfy on 2011-09-19
> what appears to be, the common problem with the nvidia driversIn particular - what problem do YOU have ?

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by owiknowi on 2011-09-19
type of computer and/or brand might come in handy too...

if your using a newer notebook with switchable graphics, e.g. a video chipset and a dedicated video card, you might want to take look here:
[http://ubuntuforums.org/showthread.php?t=1845896](http://ubuntuforums.org/showthread.php?t=1845896)

good luck and don't get confused ;)

---

### Post by easily.confused on 2011-09-19
The "driver is activated but not in use" message, which I'm quite happy to ignore but I think there is a problem somewhere because any game with above average graphics just freezes or plays really slowly, chopping and then shutting down on me.

---

### Post by Elfy on 2011-09-19
Are you using unity? That's the version with a non movable panel on the left hand side?

Open a terminal and paste ```
cat /var/log/Xorg.0.log |grep nvidia
```

Do you get an output?

---

### Post by easily.confused on 2011-09-19
I tried that and yes I got something...
grant@ubuntu:~$ cat /var/log/Xorg.0.log |grep nvidia
[    19.668] (==) Matched nvidia as autoconfigured driver 0
[    19.668] (II) LoadModule: "nvidia"
[    19.668] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.674] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.786] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.463] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    20.463] (II) NVIDIA(0):     "nvidia-auto-select"
[    20.469] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
Hope this makes sense because unfortunately its err odd to me, lol.

---

