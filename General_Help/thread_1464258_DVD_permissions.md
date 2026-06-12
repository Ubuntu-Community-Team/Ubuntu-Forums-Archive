---
title: "DVD permissions"
date: 2010-04-28
forum: General Help
---

### Post by saronoff on 2010-04-28
I get partial answers when I search Google for the issue so I figured I'd just ask exactly what I need.

Firstly, I have a mostly fresh install of Ubuntu 9.10. The only things I've added are VLC and its required packages and packages to get my wireless adapter working. I also ran a system update to get the newest set of packages installed.

I have a Dell Dimension 2400. I added a Pioneer A18M DVD Writer to it in an effort to turn the Dell in to a media center for myself and my wife. However, to make it fully functional I need to be able to watch DVDs.

Two things seem like the root of the problem. Firstly, the DVD is actually be mounted in media under "cdrom1". (I have a regular CD-ROM on the system as well) Second, when I insert a DVD the permissions on cdrom1 change from:

drwxr-xr-x 2 root root  4096 2010-04-27 17:44 cdrom1

to

dr-xr-xr-x 6 4294967295 4294967295   536 1999-08-02 17:29 cdrom1

When I go in to properties for the DVD and pull up the "Permissions" tab I get the permissions for the drive cannot be determined. I'm at a loss. Any help would be greatly appreciated.

---

### Post by 2hot6ft2 on 2010-04-28
You need the codecs to decode the dvd

This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then for dvd playback
```
sudo apt-get install libdvdcss2
```

---

