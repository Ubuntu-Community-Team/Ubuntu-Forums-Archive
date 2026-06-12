---
title: "Installing MP3 Codec"
date: 2011-06-13
forum: General Help
---

### Post by Mazate on 2011-06-13
I downloaded the free MP3 codec from Fluendo and I'm having trouble installing it on Ubuntu for some reason.  Does anyone have any suggestions on the process to follow to install it.  I prefer to install this codec to using the auto install that you're offered when in Banshee.

---

### Post by Vaphell on 2011-06-13
what's wrong with using repo version of mp3 codec?

```
$ apt-cache search fluendo
flumotion - Fluendo Streaming Server - manager, worker and admin
gstreamer0.10-fluendo-mpegdemux - GStreamer plugin for demuxing of MPEG2 streams
gstreamer0.10-fluendo-mpegmux - GStreamer plugin for muxing of MPEG2 TS streams
gstreamer0.10-fluendo-plugins-mp3-partner - MP3 codec support for GStreamer
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
**gstreamer0.10-fluendo-mp3** - Fluendo mp3 decoder GStreamer plugin
```

isn't it pretty much the same?

---

### Post by Mazate on 2011-06-13
> **Vaphell said:**
> what's wrong with using repo version of mp3 codec?

```
$ apt-cache search fluendo
flumotion - Fluendo Streaming Server - manager, worker and admin
gstreamer0.10-fluendo-mpegdemux - GStreamer plugin for demuxing of MPEG2 streams
gstreamer0.10-fluendo-mpegmux - GStreamer plugin for muxing of MPEG2 TS streams
gstreamer0.10-fluendo-plugins-mp3-partner - MP3 codec support for GStreamer
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
**gstreamer0.10-fluendo-mp3** - Fluendo mp3 decoder GStreamer plugin
```isn't it pretty much the same?

It's my understanding (correct me if I'm wrong) that when you install the repo version of the mp3 codec, it also installs other codecs with it.  I only want the fluendo mp3 codec installed and nothing else.

---

### Post by elliotn on 2011-06-13
get a deb

---

### Post by Vaphell on 2011-06-13
if you put in terminal
```
sudo apt-get install gstreamer0.10-fluendo-mp3
``` does it say it wants to download some other packages? (if you prefer gui, check that package in synaptic - what happens if you mark it to install, does it list some other packages)

---

### Post by Mazate on 2011-06-13
> **elliotn said:**
> get a deb

What is a deb?

---

### Post by Mazate on 2011-06-13
> **Vaphell said:**
> if you put in terminal
```
sudo apt-get install gstreamer0.10-fluendo-mp3
``` does it say it wants to download some other packages? (if you prefer gui, check that package in synaptic - what happens if you mark it to install, does it list some other packages)


I typed that into the terminal and got this response:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

In fact, I get that same error when I even just try to open the synaptic.  I click on it, it prompts me for the password, I enter it, synaptic opens up and I immediately get that error.  I press ok and synaptic closes.

---

### Post by mastablasta on 2011-06-13
well, it seems to me like it says what you need to do to correct the problem.

---

