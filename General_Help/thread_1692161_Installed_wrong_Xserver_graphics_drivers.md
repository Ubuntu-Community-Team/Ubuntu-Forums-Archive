---
title: "Installed wrong Xserver graphics drivers"
date: 2011-02-21
forum: General Help
---

### Post by Da CalebMan on 2011-02-21
Hey guys :),

I accidentally installed ATI graphics drivers on an intel graphics system. They didn't appear to install properly, because upon next boot everything was fine, except for compiz and any 3d game. 

compiz-check says that I've managed to get intel back as default, but I'm still missing a rendering method.

Does anyone know how to get the renderer back? I assume it has something to do with changing the kernel? I don't know how to change the kernel anyway.

Any help would be appreciated,

Caleb

---

### Post by quixote on 2011-02-23
I don't have any useful suggestions except to say that it is okay to bump your question back into "current" after a day or so of no answers. Maybe try a different subject, such as: "how to get 3D rendering with intel graphics?"  Just a suggestion.  No idea if it'll bring the experts out of the woodwork. :D

---

### Post by Da CalebMan on 2011-02-24
Thanks.:)

---

### Post by Forlong on 2011-02-24
What's the output of ```
dpkg -l | grep "fglrx\|nvidia"
``` as well as ```
cat /etc/X11/xorg.conf
```

---

### Post by clhsharky on 2011-02-24
Da CalebMan

You may need to reconfigure your video driver.
```
sudo dpkg-reconfigure xserver-xorg
```
Log off/log in


Sharky

---

### Post by Da CalebMan on 2011-02-25
```
ii  nvidia-173-modaliases                 173.14.28-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                  96.43.19-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-cg-toolkit                     3.0.0007-0ubuntu1                                 Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                         0.2.24                                            Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             260.19.06-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
```


```
cat: /etc/X11/xorg.conf: No such file or directory
```

Sharky: I've tried that command many times before, with different action options, even when X was terminated. No output displayed. Not even errors. Is that normal? :?

---

### Post by realzippy on 2011-02-25
Try:

```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```

```
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core
```



more:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by Da CalebMan on 2011-02-25
Woah, thanks guys! Whatever you did, you got it working like a charm. I'm not really sure which command did it, but I assume it had to do with reinstalling mesa-glx. Thanks again for the support

;)

---

