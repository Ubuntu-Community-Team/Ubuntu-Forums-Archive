---
title: "Pandora not working in 9.10"
date: 2009-11-27
forum: General Help
---

### Post by mwjones on 2009-11-27
I have been using Pandora as a web app for about a year now, but suddenly with my upgrade to 9.10, Pandora no longer works.  Usually I cannot even sign in.  On the rare chance that I do get the sign in screen to appear, and actually authenticate, I cannot select any channels.

Has anyone experienced this and fixed it?

Here are some relevant packages I have installed:

```
$ sudo dpkg -l | grep -i flash
ii  flashplugin-installer                10.0.32.18ubuntu1                          Adobe Flash Player plugin installer
$ sudo dpkg -l | grep -i firefox
ii  firefox                              3.5.5+nobinonly-0ubuntu0.9.10.1            meta package for the popular mozilla web bro
ii  firefox-3.5                          3.5.5+nobinonly-0ubuntu0.9.10.1            safe and easy web browser from Mozilla
ii  firefox-3.5-branding                 3.5.5+nobinonly-0ubuntu0.9.10.1            Package that ships the firefox branding
ii  firefox-3.5-gnome-support            3.5.5+nobinonly-0ubuntu0.9.10.1            Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                3.5.5+nobinonly-0ubuntu0.9.10.1            meta package pointing to the latest gnome-su
ii  ubufox                               0.8-0ubuntu1                               Ubuntu Firefox specific configuration defaul
```

uname -a:
```
$ uname -a
Linux raven 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
```

---

### Post by mwjones on 2009-11-27
I tried installing the library straight from Adobe, but that doesn't work.  Their documentation on the simple install procedure isn't even accurate.  What a bunch of wankers.

---

### Post by mwjones on 2009-11-27
I also tried the instructions from [http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml) 

YouTube works alright, but sites like Pandora and Hulu do not.

[IMG]http://images.encyclopediadramatica.com/images/b/b6/FFFFFFFFFFFFFFFFUUUUUUUUUUUUUUUUU.JPG[/IMG]

---

### Post by mwjones on 2009-11-28
No love? :(

---

### Post by darco on 2009-11-28
Running x64 with Chromium and Pandora/Hula are fine. I know there was a issue for flash where you had to right click a flash button, then move the cursor away from the button then left click an open area, then you could go back and left click button and it would work fine. That is no longer the issue but I dont know if it was a chromium issue or a flash issue. Try it.
Also this link is to install x64 flash, works perfect

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

good luck

darco

---

### Post by mwjones on 2009-11-29
That seems to have worked, thanks!  It appears this was the part I was missing:

```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
```

---

