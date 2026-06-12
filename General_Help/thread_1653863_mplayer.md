---
title: "mplayer"
date: 2010-12-27
forum: General Help
---

### Post by mIXpRo on 2010-12-27
hii , could someone point me to a tutorial on installing mplayer with all the codecs and a graphical ui
, cause i'm not finding one here . and pls [COLOR=Red]don't direct me to the documentation on there site cause i've tried a lot there and i hated it .[/COLOR]

---

### Post by deserthowler on 2010-12-27
have you tried Medibuntu?

Earl

---

### Post by mIXpRo on 2010-12-27
installed medibuntu then what ?

---

### Post by jmszr on 2010-12-27
mIXpRo,

I would suggest installing these ppa's: [https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=lucid](https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=lucid) and: [https://launchpad.net/~rvm/+archive/smplayer?field.series_filter=lucid](https://launchpad.net/~rvm/+archive/smplayer?field.series_filter=lucid) 

After installing these and running "sudo apt-get update" they (mplayer and smplayer [gui frontend]) will be available for installation in the Update Manager.

Edit: These are for 10.04 but they are available for other releases.

---

### Post by veggen on 2010-12-27
I just installed Ubuntu restricted extras and Gnome MPlayer (looks much better in Gnome than SMplayer), both from the repos. All works fine for over a year now.

---

### Post by mIXpRo on 2010-12-27
when i try to run mplayer with gui "gmplayer" , i get :
```

gmplayer: relocation error: gmplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

```

---

### Post by mc4man on 2010-12-27
That error is typical of having ffmpeg shared libraries that are mismatched to those your mplayer was built off of.
(most ubuntu repo mplayer builds depend on shared ffmpeg libraries 

You haven't mentioned what release of ubuntu you're using...

---

### Post by foxmulder881 on 2010-12-27
There's no need to even use Medibuntu for MPlayer anymore as it's in the Universe repo. I just did this:

```
sudo aptitude install gnome-mplayer
```

Done. Installed and working.

---

### Post by mIXpRo on 2010-12-27
> **mc4man said:**
> That error is typical of having ffmpeg shared libraries that are mismatched to those your mplayer was built off of.
(most ubuntu repo mplayer builds depend on shared ffmpeg libraries 

You haven't mentioned what release of ubuntu you're using...

i'm using lucid lynx 10.04

---

### Post by mc4man on 2010-12-27
As I recollect you posted in the svn mplayer how-to and there was some conflicting stuff about what mplayer source you where building ect.

A simple solution that bypasses whatever you've done previously, whether you have ppa packages, whatever

Search mplayer in synaptic, remove any and all mplayer packages.

When done open a terminal, run mplayer - it should show not installed. If anything comes up then likely there are mplayer libraries in /usr/local/*
(if so browse to and remove.

Then open software sources and add this ppa ( highly trusted, provides a new mplayer build every 3 days or so, you don't have to update that often 
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

Then click close and reload

The ppa does provide the older gui, try that and or gnome-mplayer

So from terminal (for old gui

```
sudo apt-get install mplayer-gui
```
or 
```
sudo apt-get install gnome-mplayer
```

This mplayer build uses it's own ffmpeg lib's so there will be no conflict

---

### Post by mIXpRo on 2010-12-28
i get this when i try to play this stream :

```

mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-7.wmv

```

on mplayer-gui :
```

MPlayer SVN-r32734-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-7.wmv.
STREAM_ASF, URL: mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-7.wmv
Resolving video9.technion.ac.il for AF_INET6...

Couldn't resolve name for AF_INET6: video9.technion.ac.il
Resolving video9.technion.ac.il for AF_INET...
Connecting to server video9.technion.ac.il[132.68.1.27]: 1755...

connect error: Connection timed out
Resolving video9.technion.ac.il for AF_INET6...

Couldn't resolve name for AF_INET6: video9.technion.ac.il
Resolving video9.technion.ac.il for AF_INET...
Connecting to server video9.technion.ac.il[132.68.1.27]: 80...
read: Resource temporarily unavailable

Failed, exiting.
Resolving video9.technion.ac.il for AF_INET6...

Couldn't resolve name for AF_INET6: video9.technion.ac.il
Resolving video9.technion.ac.il for AF_INET...
Connecting to server video9.technion.ac.il[132.68.1.27]: 80...

Read failed.
No stream found to handle url mms://video9.technion.ac.il/Courses/Hozek1/Hozek1-7.wmv

[mw] event none received.

```

on gnome-mplayer :
```

media size = 0 x 0
media size = 316 x 19

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(gnome-mplayer:4163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
media size = 372 x 10

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-mplayer:4163): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(gnome-mplayer:4163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
media size = 316 x 23

```

---

