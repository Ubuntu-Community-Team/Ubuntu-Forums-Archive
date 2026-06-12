---
title: "WMV files don't plays in Totem"
date: 2010-08-12
forum: General Help
---

### Post by krishnandu.sarkar on 2010-08-12
Hey friends, I want to play .wmv files. I can play them in VLC successfullt but they are not getting played in Totem. I've installed all the codecs. What to do??

---

### Post by ronnielsen1 on 2010-08-12
Have you installed totem-xine?

---

### Post by krishnandu.sarkar on 2010-08-12
No. Do I need to install that in able to play WMV files?? What is totem-xine??

---

### Post by bobcollard on 2010-08-12
totem-xine is a firefox plugin.  You could just install gxine and get he same results, something that will open windows media.

---

### Post by krishnandu.sarkar on 2010-08-12
you mean sudo apt-get install gxine. But what is this xine?? I heard it's a media player.

---

### Post by bobcollard on 2010-08-12
> **krishnandu.sarkar said:**
> you mean sudo apt-get install gxine. But what is this xine?? I heard it's a media player.
xine is a plugin used to open (g)xine media player.  (Gnome)xine.   Totem is another media player.

---

### Post by krishnandu.sarkar on 2010-08-12
Ok But I don't have this media player installed. So what's the point of installing that plugin??

---

### Post by krishnandu.sarkar on 2010-08-12
BTW I tried installing both totem-xine and gxine, but nothing helped. I can play .wmv files on VLC but why not on Totem?? I don't think this is a codec problem...then why would it get played in VLC??

---

### Post by -Robert- on 2010-08-12
Did you install the ubuntu-restricted-extras package? Also read this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bobcollard on 2010-08-12
> **krishnandu.sarkar said:**
> BTW I tried installing both totem-xine and gxine, but nothing helped. I can play .wmv files on VLC but why not on Totem?? I don't think this is a codec problem...then why would it get played in VLC??
Did you restart Firefox?

---

### Post by jcolyn on 2010-08-12
> **krishnandu.sarkar said:**
>  I can play .wmv files on VLC but why not on Totem?? I don't think this is a codec problem...then why would it get played in VLC??

I can't understand why totem is still being used. It won't open much of anything. My solution is to uninstall totem and install gecko. Click the below link and scroll part way down to my solution.

Gnome Mplayer will play wmv files I just tried it..

[http://ubuntuforums.org/showthread.php?t=1549431](http://ubuntuforums.org/showthread.php?t=1549431)

---

### Post by andrew.46 on 2010-08-12
Hi krishnandu,

> **krishnandu.sarkar said:**
> Hey friends, I want to play .wmv files. I can play them in VLC successfullt but they are not getting played in Totem. I've installed all the codecs. What to do??

Can you post a link to some of these troublesome wmv files?

Andrew

---

### Post by krishnandu.sarkar on 2010-08-12
> **andrew.46 said:**
> Hi krishnandu,



Can you post a link to some of these troublesome wmv files?

Andrew

Hehehe...lol...I can't. They are on my HDD. And all are XXX Videos. :P :D

---

### Post by krishnandu.sarkar on 2010-08-13
> **-Robert- said:**
> Did you install the ubuntu-restricted-extras package? Also read this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I didn't installed ubuntu-restricted-extras. But when I installed Ubuntu and tried to play the files for first time, it automatically searched and installed the required codecs. After that everything was going fine. But day before yesterday I got bored with default GNOME and installed KDE and that's where all these problems started. And by going to remove kubuntu-desktop, I removed many other packages. Some of them are Wine, LAMP-server etc. I installed them again but no idea why don't wmv files are not getting played in totem but in VLC.

> **bobcollard said:**
> Did you restart Firefox?

No. :(

Ok...I'm trying again.

---

### Post by Bradtek on 2010-08-13
You could also try
```
sudo apt-get install w32codecs
```

---

### Post by krishnandu.sarkar on 2010-08-13
> **Bradtek said:**
> You could also try
```
sudo apt-get install w32codecs
```


I tried this before also. But I get this :

```
sudo apt-get install w32codecs
[sudo] password for krishnandu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

---

### Post by krishnandu.sarkar on 2010-08-13
Guys...I thought after all these may be installing ubuntu-restricted-extras would be much better option.

I ran ubuntu-restricted-extras and got these packages
  ca-certificates-java freepats gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin libaccess-bridge-java
  libaccess-bridge-java-jni libcdaudio1 libcelt0-0 libfftw3-3 libflite1
  libgme0 libiptcdata0 libkate1 libmimic0 libmms0 libmp4v2-0 libofa0
  libopenspc0 liborc-0.4-0 libsoundtouch1c2 libwildmidi0 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib tzdata-java
  ubuntu-restricted-extras unrar

I've installed JDK. To avoid any problems...I manually installed gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse libcdaudio1 libcelt0-0 libfftw3-3 libflite1 libgme0 libiptcdata0 libkate1 libmimic0 libmms0 libmp4v2-0 libofa0


But that too didn't helped. :(

---

### Post by bobcollard on 2010-08-13
Sounds like you lost a lot more than you thought when you uninstalled KDE.  I would advise a backup of home directory and clean install of ubuntu.

---

### Post by krishnandu.sarkar on 2010-08-13
Hmmm...May be true...So there is no other way out?? I'm not going to re-install everything for playing wmv files in Totem. I'll make it up with VLC if no other way comes out.

---

