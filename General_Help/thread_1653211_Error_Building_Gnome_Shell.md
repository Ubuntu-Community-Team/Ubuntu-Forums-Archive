---
title: "Error Building Gnome Shell"
date: 2010-12-26
forum: General Help
---

### Post by MrRichard on 2010-12-26
Hi, I get this error when building the latest and greatest Gnome Shell on process [13/33]:

(this is just a snippet of the torrent of text spewing out of the terminal)

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


Is there any way I can install glxCreateContext or fix this issue?

---

### Post by dino99 on 2010-12-26
8 hours ago :)

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by MrRichard on 2010-12-26
> **dino99 said:**
> 8 hours ago :)

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

Hey, thanks for the reply. :)
To install gnome-shell, do you simply add the above PPA and install the gnome-shell package?

---

### Post by dino99 on 2010-12-26
yeah, read explanations given on that ppa page :)

---

### Post by MrRichard on 2010-12-27
Unfortunately, I don't think I know what I'm doing so it's best not to install Gnome Shell for now.

Thanks for your help anyways :).

---

### Post by MrRichard on 2010-12-27
Unfortunately, I don't think I know what I'm doing so it's best not to install Gnome Shell for now.

Thanks for your help anyways :).

---

### Post by MrRichard on 2010-12-27
Unfortunately, I don't think I know what I'm doing so it's best not to install Gnome Shell for now.

Thanks for your help anyways :).

Woah! I didn't mean to post all of these responses :-s

---

### Post by Harry33 on 2010-12-27
Installing Ricotz testing PPA will at least in Natty -alfa1 break gdm theming and desktop theming. This is because new Gnome-Shell needs the package gnome-settings-daemon_2.91.*

---

