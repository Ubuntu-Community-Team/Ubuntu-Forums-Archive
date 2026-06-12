---
title: "What makes Ubuntu so heavy?"
date: 2011-10-06
forum: General Help
---

### Post by erbad on 2011-10-06
I downloaded Ubuntu, applied all of the updates and installed just four applications (Remastersys, VLC, Filezilla and Google Chrome).  When I use remastersys to create an image of my distro, it comes out to about 1.1 Gig.

I really wanted to drop the size of this distro so using Ubuntu Software Centre, I removed all of the games, OpenOffice, the media player, simple scan, bluetooth, Firefox and a whole host of other apps.

Now when I use remastersys, the size of my distro is 950MB.  I'd really like to drop the size of the distro to under 600MB or even smaller.  What else can I remove to accomplish this task?

Thank you

---

### Post by josephellengar on 2011-10-06
> **erbad said:**
> I downloaded Ubuntu, applied all of the updates and installed just four applications (Remastersys, VLC, Filezilla and Google Chrome).

When I use remastersys to create at image of my distro, it comes out to about 1.1 Gig.

I really wanted to drop the size of this distro so using Ubuntu Software Centre, I removed all of the games, OpenOffice, the media player, simple scan, bluetooth, Firefox and a whole host of other apps.

Now when I use remastersys, the size of my distro is 950MB.

I'd really like to drop the size of the distro to under 600MB or even smaller.  What else can I remove to accomplish this task?

Thank you

Remove your Desktop Environment (probably Gnome) and use Ratpoison or something similar? Or maybe XFCE; I think that that's only ~50mb and has almost as much functionality as Gnome.

---

### Post by robert shearer on 2011-10-06
If you have applied updates then there will still be old package versions in cache.

Clean up by doing the following..
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

each will remove progressively more packages with the first two being safe to run and the last only if you have a working system with the current kernel.
 It will remove the older kernels and **all** older packages in cache.

See what that reduces it by.

However, and I may be wrong here, I believe the standard Ubuntu cd Iso is compressed and unpacked as you install it. (look at the installed filesystem size in system monitor window vs the install cd image size)

Remastersys will make a live cd/dvd of the unpacked o/s so it will **never** be as small as an Ubuntu install cd without removing most of the packages and desktop.

---

### Post by bodhi.zazen on 2011-10-06
> **erbad said:**
> I downloaded Ubuntu, applied all of the updates and installed just four applications (Remastersys, VLC, Filezilla and Google Chrome).  When I use remastersys to create an image of my distro, it comes out to about 1.1 Gig.

I really wanted to drop the size of this distro so using Ubuntu Software Centre, I removed all of the games, OpenOffice, the media player, simple scan, bluetooth, Firefox and a whole host of other apps.

Now when I use remastersys, the size of my distro is 950MB.  I'd really like to drop the size of the distro to under 600MB or even smaller.  What else can I remove to accomplish this task?

Thank you

You are going about it the wrong way. Use the debian live scripts.

---

### Post by 3rdalbum on 2011-10-07
Have you possibly got all the language packs installed? They don't ship on the CD but are downloaded during the installation process. Remove those and you free up a ton of space.

---

### Post by vasa1 on 2011-10-07
> **3rdalbum said:**
> Have you possibly got all the language packs installed? They don't ship on the CD but are downloaded during the installation process. Remove those and you free up a ton of space.

How can we know this? I know that when I installed 11.04 for the first time recently the downloading of language packs seemed to be a major aspect. What is the safe way to remove the unwanted ones, assuming English GB or US is only what I need?

---

### Post by elliotn on 2011-10-07
> **bodhi.zazen said:**
> You are going about it the wrong way. Use the debian live scripts.

debian script.
elaborate please

---

### Post by jazzon on 2011-10-07
remaster sys has vanished.  As in in no longer being maintained or distrubeted.  If you still have the deb file (and its 32 bit lucid version) I would love it if you could get in touch with me as i need it.  Feel free to PM me with a response.

---

### Post by vasa1 on 2011-10-07
> **3rdalbum said:**
> Have you possibly got all the language packs installed? They don't ship on the CD but are downloaded during the installation process. Remove those and you free up a ton of space.

Will this ([http://www.linuxformat.com/forums/viewtopic.php?p=89055](http://www.linuxformat.com/forums/viewtopic.php?p=89055)) be helpful for the *next* install?

---

### Post by LowSky on 2011-10-07
or use the fork

[http://re-linux.sourceforge.net/](http://re-linux.sourceforge.net/)

---

### Post by JSchultheis on 2011-10-07
There is always the option of going with a light build from the start:
ubuntu: gnome 
kubuntu: kde
lubuntu: lxde
peppermint os: even lighter weight LXDE

All are debian Ubuntu derivatives. I run with Peppermint OS.

---

### Post by bodhi.zazen on 2011-10-07
> **elliotn said:**
> debian script.
elaborate please

[http://live.debian.net/](http://live.debian.net/)

[http://live.debian.net/manual/de/html/index.html](http://live.debian.net/manual/de/html/index.html)

The packages are in the ubuntu repositories.

There is a bit of a learning curve when making a live CD, but the live scripts are by far the most automated and give the best results.

Remastersys is "OK", but if the resulting image is too large, it is going to be clumsy to start removing things.

---

