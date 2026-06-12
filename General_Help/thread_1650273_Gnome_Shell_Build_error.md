---
title: "Gnome Shell Build error"
date: 2010-12-21
forum: General Help
---

### Post by MrRichard on 2010-12-21
Hi, as the build progress was under way, this error came from the terminal:
```
checking GL/glx.h presence... yes
checking for GL/glx.h... yes
checking for glXCreateContext in -lGL... no
configure: error: Required GLX library not found
*** Error during phase configure of clutter: ########## Error running ./autogen.sh --prefix /home/richard/gnome-shell/install --libdir '/home/richard/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [13/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 

```

I've tried choice 6 with no luck. The machine is using an up-to-date Ubuntu 10.10 and an ATI 5830 (if it matters ;)).

Any suggestions?

---

### Post by WorMzy on 2010-12-21
```
sudo apt-get install gnome-shell
```?

---

### Post by MrRichard on 2010-12-21
I tried that, but it seems a bit out of date. Or is that the most stable version of Gnome Shell, and the one I'm trying to install the unstable version?

---

