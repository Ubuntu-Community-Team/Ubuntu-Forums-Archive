---
title: "problem installing yudit 2.9.2 on 9.10 koala"
date: 2010-02-17
forum: General Help
---

### Post by scrad on 2010-02-17
Hi ... pitiful n00b here,
I am attempting to install the latest 'yudit', and I have downloaded and installed yudit 2.9.2. But get following error:

    **~ >>** yudit
    AWT is not implemented on this platform.
    This can happen if X11 Development libraries
    were missing when configure was executed.

But when attempting to apt-get install x11-common I am told that x11-common is already the newest version.

My question is - How do I install the 'X11 Development libraries' that I seem to need ?

    ~ >> java -version
    java version "1.6.0_15"
    Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
    Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

(I don't know if this is relevant but I am running a 32-bit koala on a AMD64-bit laptop)

Many thanks

---

### Post by darolu on 2010-02-17
Try with:
```
$ sudo apt-get install libx11-dev
```

Other X11-dev packages:
```
$ sudo apt-get install libghc6-x11-dev libgl1-mesa-swx11-dev
```

---

### Post by scrad on 2010-02-17
Thanks !! That did the trick and it works now.

It seems that I had already somehow installed 'libx11-dev'
but not the additional packages. They made the difference.

Many thanks for the quick reply. That's great.

---

