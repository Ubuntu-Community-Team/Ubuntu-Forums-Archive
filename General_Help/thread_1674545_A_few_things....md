---
title: "A few things..."
date: 2011-01-24
forum: General Help
---

### Post by n00blit on 2011-01-24
Hi,

I have Ubuntu Gnome v10.4.

I need to download the 56k Modem driver, MP3 codec, and WINE.

I live in a place that only has Dial up I need to downloads the files separately i.e not through Linux, just something to put on my USB stick...any ideas???

---

### Post by djeikyb on 2011-01-24
Tisn't really the best way of doing it, but you can download the deb packages from: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

May be a bit tricky, cause you'll need to download not only the packages you want, but their dependencies also. For example, say you want emacs, the ever popular editor that many people mistakenly claim is better than vim. This is just a meta package(1), you really want one of the three other emacs packages it lists. Let's say you want emacs with gtk+(2) support. Now look at the dependencies for the emacs+gtk. Looks like there's over twenty of them. You could download them all, or take notes on which you've already got installed, which you don't have, and which need upgrading.

You can install the debs with dpkg. Please, read the man page first. I don't claim to be an expert. All I know is you can run this command and Ubuntu will attempt to extract and install the deb:```
dpkg -i emacs23_23.1+1-4ubuntu7_i386.deb
```

1. [http://packages.ubuntu.com/lucid/editors/emacs](http://packages.ubuntu.com/lucid/editors/emacs)
2. [http://packages.ubuntu.com/lucid/emacs23](http://packages.ubuntu.com/lucid/emacs23)

---

