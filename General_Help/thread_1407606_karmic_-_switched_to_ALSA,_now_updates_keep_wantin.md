---
title: "karmic - switched to ALSA, now updates keep wanting to reinstall pulseaudio"
date: 2010-02-15
forum: General Help
---

### Post by alldaylong on 2010-02-15
Hey all,

I was having trouble with sound and jack logic, so i switched to alsa from pulseaudio. Now every time I update I have to uncheck any pulseaudio packages.

I tried to remove the remaining pulseaudio pieces from synaptic, but it wants to remove things that totally shouldn't be removed, like gnome-session, and lmms, etc.

Is there another way to purge my comp of this plague known as pulseaudio?

---

### Post by alldaylong on 2010-02-15
The two packages I want to remove are

libpulse0
libpulse-mainloop-glib0

but here's what synaptic wants to do

```
:~$ sudo apt-get remove libpulse0
...
The following packages will be REMOVED:
  cervisia cvsservice devede gnome-applets gnome-control-center gnome-media
  gnome-orca gnome-panel gnome-session gnome-settings-daemon indicator-applet
  indicator-applet-session indicator-messages indicator-session
  kdebase-runtime kdebase-runtime-bin-kde4 khelpcenter4 kompare ktouch
  libasound2-plugins libfluidsynth1 libpulse-mainloop-glib0 libpulse0 libxine1
  libxine1-misc-plugins lmms mencoder mplayer-nogui phonon-backend-xine
  python-speechd speech-dispatcher

```

Pretty sure proceeding would be a bad idea.

---

### Post by alldaylong on 2010-02-27
can anyone help me with this please? any pointers would be greatly appreciated.

---

### Post by ell02 on 2010-02-27
I used this guide to remove pulse.Since then there have been no issues due to updates.[http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse)

---

