---
title: "Black Login Screen"
date: 2010-01-30
forum: General Help
---

### Post by Takkak on 2010-01-30
Well, I recently switched from ubuntu to xubuntu, and I was playing around. I found the /usr/share/xfce4/backdrops folder and I decided to put my own backdrops there. I deleted the old ones. I logged out and realized the background to the login screen was gone.

Can someone tell me the original name of the login screen image file or another way to fix it please? :o

---

### Post by Takkak on 2010-01-31
Hm, I reinstalled xubuntu-artwork and xubuntu-wallpapers but still nothing :/

---

### Post by Takkak on 2010-02-01
Bump!

---

### Post by Takkak on 2010-02-02
Anyone?

---

### Post by Takkak on 2010-02-07
..please help?

---

### Post by Takkak on 2010-02-07
rebump

---

### Post by Oatworm on 2010-02-08
I'd look at the following:

[LIST=1]
[*]Are your permissions correct?  Looking at my installation, all of the backdrop files are owned by root/root and show 644 permissions.
[*]Go to /var/cache/apt/archives and see if the xubuntu-wallpapers package is in there.  If it is, copy it to your home folder and extract it.  Then, copy the files from the extracted file to the original backdrop source, being sure to adjust permissions once you're done.
[/LIST]

**Permissions**
To check your permissions, cd to */usr/share/xfce4/backdrops*, then type the following:
```
ls -la
```

You should see something that looks like the following:
```
foo@bar:/usr/share/xfce4/backdrops$ ls -la
total 10116
drwxr-xr-x 2 root root    4096 2010-01-26 08:03 .
drwxr-xr-x 9 root root    4096 2010-01-26 08:03 ..
-rw-r--r-- 1 root root  557451 2009-10-06 06:03 flower.png
-rw-r--r-- 1 root root  112588 2009-10-06 06:03 xfce4gradientcurve.png
-rw-r--r-- 1 root root   52177 2009-10-06 06:03 xfce4logo.png
-rw-r--r-- 1 root root   22700 2009-10-06 06:03 xfce-in-a-grid.png
-rw-r--r-- 1 root root  254915 2009-10-06 06:03 xfce-in-the-moon.png
-rw-r--r-- 1 root root  190400 2009-10-06 06:03 xfce-smoke.png
-rw-r--r-- 1 root root     850 2009-10-06 06:03 xfce-stellar-tile.png
-rw-r--r-- 1 root root  137214 2009-10-06 06:03 xfce-stripes.png
-rw-r--r-- 1 root root  364278 2009-10-06 06:03 xfce-turbulence.png
-rw-r--r-- 1 root root 1153487 2009-10-10 13:57 xubuntu-jaunty.png
-rw-r--r-- 1 root root  860239 2009-10-10 13:57 xubuntu-jaunty-ws.png
-rw-r--r-- 1 root root  674590 2009-10-10 13:57 xubuntu-jmak-edgy.png
-rw-r--r-- 1 root root  433425 2009-10-10 13:57 xubuntu-jmak-feisty.png
-rw-r--r-- 1 root root  293713 2009-10-10 13:57 xubuntu-jmak-gutsy.png
-rw-r--r-- 1 root root  739373 2009-10-10 13:57 xubuntu-jmak-hardy.png
-rw-r--r-- 1 root root  867482 2009-10-10 13:57 xubuntu-jmak.png
-rw-r--r-- 1 root root  850525 2009-10-10 13:57 xubuntu-jmak-ws.png
-rw-r--r-- 1 root root 1059202 2009-10-10 13:57 xubuntu-karmic-gdm.png
-rw-r--r-- 1 root root 1059202 2009-10-10 13:57 xubuntu-karmic.png
-rw-r--r-- 1 root root  366618 2009-10-10 13:57 xubuntu-luzi.png
-rw-r--r-- 1 root root  259722 2009-10-10 13:57 xubuntu-steel.png

```

If you don't, either use *chown* to change the owner back to root (i.e. from within the folder, type *sudo chown root *.png*), *chgrp* to change the group back to root (i.e. *sudo chgrp root *.png*), or *chmod* to set the permissions back to what they should be (i.e. from within the directory, *sudo chmod 644 *.png*).

**Extract the Archive**

If that doesn't work, you may still have the archive saved from your last installation attempt.  If so, it'll be in */var/cache/apt/archives*.  If it's not, just type the following to download it:
```
sudo apt-get -d install xubuntu-artwork --reinstall
```
That'll download the package; the -d tells it to download only but not install.  Once it's downloaded and placed in the */var/cache/apt/archives* folder, you can then run the following command to extract the contents to a subfolder in your home directory:
```
sudo dpkg-deb -x xubuntu-wallpapers_0.38_all.deb ~/xubuntuartwork
```
Note that the "xubuntu-artwork_..." package name should match the name of the package in your */var/cache/apt/archives*, and that the command will extract the contents of the package to the /xubuntuartwork folder in your home directory.

Once the extraction is complete, if you go to your home folder, you'll find all of the wallpaper that you just deleted.

Enjoy!

---

