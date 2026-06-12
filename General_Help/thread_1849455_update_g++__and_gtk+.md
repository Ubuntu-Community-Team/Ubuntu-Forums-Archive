---
title: "update g++  and gtk+?"
date: 2011-09-24
forum: General Help
---

### Post by jinjin on 2011-09-24
1) how do i update my g++ compiler on ubuntu 10.04?

2) i currently have gtk+ version 2.10, how do i update that to version 2.24? 

thanks

---

### Post by dniMretsaM on 2011-09-24
If you have the highest version that are in the repos, you'll have to download and compile. The latest version of GCC (includes g++) can be found [here]("http://gcc.gnu.org/") and you can download the latest GTK+2 version [here]("http://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/") ([direct link to version 2.24.6]("http://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/gtk+-2.24.6.tar.bz2")). Don't know how to compile? [Click me.](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by jinjin on 2011-09-24
> **dniMretsaM said:**
> If you have the highest version that are in the repos, you'll have to download and compile. The latest version of GCC (includes g++) can be found [here]("http://gcc.gnu.org/") and you can download the latest GTK+2 version [here]("http://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/") ([direct link to version 2.24.6]("http://ftp.gnome.org/pub/gnome/sources/gtk+/2.24/gtk+-2.24.6.tar.bz2")). Don't know how to compile? [Click me.]("https://help.ubuntu.com/community/CompilingEasyHowTo")
if i compile and run the gtk+2 package you gave me, it will replace the older version with this new version?  or do i have to uninstall the old version first?

thanks

---

### Post by dniMretsaM on 2011-09-24
Don't uninstall the older version first. That would be bad. When you run [FONT=Courier New]checkinstall[/FONT] (following the instructions in the guide I linked you to), there will be some fields to insert info into. In the "Replaces" field, put the name of the old GTK+ package in there along with [FONT=Courier New]<<2.24.6[/FONT] so that it will know to remove the older version. Also give it the same dependencies as the original package. Along the way you may get some errors saying that it's trying to replace something installed by another package, simply run [FONT=Courier New]checkinstall[/FONT] again and add the name of that package to the "Replaces" field. I have never compiled a new version of GUI libraries, so these instructions may not be exactly right. This process might involve a little bit of trial-and-error on your part. Obviously you should read the README and INSTALL files that come with the package. Also, back up your data!! Good luck!

---

