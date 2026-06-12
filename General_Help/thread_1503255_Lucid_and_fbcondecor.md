---
title: "Lucid and fbcondecor"
date: 2010-06-06
forum: General Help
---

### Post by echo6 on 2010-06-06
Has anyone had any success getting splashutils to compile on Lucid?

Seeing as [ftp://ftp.berlios.de/pub/fbsplash/debian/splashutils/](ftp://ftp.berlios.de/pub/fbsplash/debian/splashutils/) packages are getting a bit long in the tooth and trying to compile from source has been a headache.

I miss not having background images on my virtual terminals :-(

---

### Post by echo6 on 2010-06-29
Finally thanks to Michal Januszewski the author I was able to compile splashutils.

sudo apt-get install libklibc-dev

I had to edit the splash_manager script to include the correct paths for the install binaries. I also had to manually install [fbres]("http://dev.gentoo.org/~spock/projects/fbsplash/archive/miscsplashutils-0.1.8.tar.bz2").

---

### Post by Karl1982 on 2010-10-05
What instructions did you follow?  I've been trying to figure this one out for a while.  I got to the point of downloading the kernel patch and discovered there's no patch for the updated kernel my test machine has (2.6.32-25-generic).  My ultimate goal is to make a nice backdrop in GIMP and eventually make it into a console background for a box with no GUI.

If you've got this figured out for Lucid LTS, you should consider writing an updated step-by-step tutorial on it.

---

### Post by echo6 on 2011-05-09
I finally got around to documenting it, but for Natty Narwal (11.04) This will also work for Lucid, only you do not need to create the symlink for klibc.

[http://ubuntuforums.org/showthread.php?t=1752196](http://ubuntuforums.org/showthread.php?t=1752196)

---

