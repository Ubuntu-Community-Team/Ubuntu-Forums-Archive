---
title: "Digikam does not show photos"
date: 2010-10-12
forum: General Help
---

### Post by gredawarha on 2010-10-12
Hello all

I have been organising some of my photos and as a KDE user I have installed Digikam.

The installation works fine, but when I load Digikam it does not show all of the photo albums in /home/darren/pictures and those albums that it does list have no photos in them.

I am sure I am probably doing something wrong but so far I have been unable to "google" a fix, cananyone help.

Also my requirements are fairly limited I use GIMP to do any editing.  But need to be able upload to Picasa

---

### Post by zyberwoof on 2010-10-12
I'm going to bump this because I'm having the same problem.  I'm using Ubuntu 10.04 (not kubuntu).  I just installed it by adding the following to my sources list:

```
deb http://ppa.launchpad.net/philip5/kde45/ubuntu lucid main
deb http://ppa.launchpad.net/philip5/extra/ubuntu lucid main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu lucid main
```

From there I just did an ```
apt-get update; apt-get install digikam kipi-plugins
```  This installed digikam 1.5 over my previous 1.2 installation.

The application opens and lists all of my albums and tags, but it doesn't display any photos.


Edit: This problem went away for me after I ran ```
apt-get upgrade
reboot
```

---

### Post by gredawarha on 2010-10-12
Thanks i will give your method a go.

---

### Post by gredawarha on 2010-10-12
Just tried what you suggested, no change.  Any ideas?

---

### Post by todak on 2010-10-12
With digiKam running, go to *Settings> Configure digiKam*. On the left side click on *Collections*. On the right side will be an option to add a collection from a local source. Click on the *Add Collection* button and you will be presented with a window to navigate to whatever folder you store your images. Choose the folder and click the *OK* button and your collection will be added. It is the process I used. See if it works for you.

---

### Post by gredawarha on 2010-10-12
Hi todak, tried that, nothing same as before, very frustrating

---

