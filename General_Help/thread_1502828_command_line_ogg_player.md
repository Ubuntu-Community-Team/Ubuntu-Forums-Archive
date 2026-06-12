---
title: "command line ogg player"
date: 2010-06-06
forum: General Help
---

### Post by perky on 2010-06-06
Is there a command-line application that can play an .ogg file?

There is a catch to this question:  the program must be shipped with Ubuntu by default (ie, must be something you can use without installing anything).

I originally thought mplayer but not 100% sure if this is shipped with Ubuntu by default?

Many thanks

---

### Post by stderr on 2010-06-06
```
canberra-gtk-play --file=/path/to/the.ogg
```

This works, but the catch is if the user has disabled system alert sounds (System->Preferences->Volume Control, Sound theme: No theme), you'll get:

```
canberra-gtk-play --file=/media/Music/Tromboon-sample.ogg
Failed to play sound: Sound disabled
```

and secondly the playback volume depends on the system sound alert volume.

---

### Post by HermanAB on 2010-06-06
ogg123
sox

---

### Post by perky on 2010-06-06
> **stderr said:**
> ```
canberra-gtk-play --file=/path/to/the.ogg
```

This works, but the catch is if the user has disabled system alert sounds (System->Preferences->Volume Control, Sound theme: No theme), you'll get:

```
canberra-gtk-play --file=/media/Music/Tromboon-sample.ogg
Failed to play sound: Sound disabled
```

and secondly the playback volume depends on the system sound alert volume.
Thanks, almost what I was after, but the sound needs to be played regardless of sound preferences.

> **HermanAB said:**
> ogg123
sox
Unfortunately, these don't come with Ubuntu by default :/

---

### Post by stderr on 2010-06-06
Hard to please, eh? ;) Well, maybe you could borrow a file from libvorbisidec-dev and use it in conjunction with aplay (I got the idea from [here]("http://www.hermann-uwe.de/taxonomy/term/1669")). You'd need to check the licence of the package libvorbisidec-dev though.

You install the package
```
sudo apt-get install libvorbisidec-dev
```

Grab the "magic" file, something like this:
```
cd /usr/share/doc/libvorbisidec-dev/examples
sudo make
sudo cp ivorbisfile_example ~
cd
sudo chown USERNAME:USERNAME ivorbisfile_example

```

Then you use that file in conjunction with aplay to play .oggs
```
cat my.ogg | ~/ivorbisfile_example | aplay -f cd
```

---

### Post by perky on 2010-06-06
> **stderr said:**
> Hard to please, eh? ;)

In this case yes :)  But I will mark this thread as solved, thanks for the suggestions!

This seems to do what I'm after, not 100% sure that it comes with Ubuntu by default though:

```
gst-launch-0.10 playbin uri=file:///usr/share/sounds/ubuntu/stereo/dialog-warning.ogg
```

[[via]("http://www.embeddedlinuxprimer.com/node/41")]

Reason for this request?  I'm making an app that plays a sound (default warning sound), and it is much easier/simpler to make a call to something that comes with Ubuntu by default rather than writing a basic media player in Python.

---

### Post by stderr on 2010-06-06
Hmm, well that works on my system too. 

If you're just using a few short alert sounds, it may be easier and more compatible to convert them to formats playable by aplay, or to use the file from libvorbisidec-dev. But your solution seems fine...

gst-launch-0.10 is contained in [gstreamer0.10-tools]("http://packages.ubuntu.com/karmic/utils/gstreamer0.10-tools"), and whilst I'm not sure either, I think it's highly likely to be included in Ubuntu by default, especially considering totem uses the gstreamer backend by default.

---

### Post by perky on 2010-06-07
> **stderr said:**
> Hmm, well that works on my system too. 

If you're just using a few short alert sounds, it may be easier and more compatible to convert them to formats playable by aplay, or to use the file from libvorbisidec-dev. But your solution seems fine...

gst-launch-0.10 is contained in [gstreamer0.10-tools]("http://packages.ubuntu.com/karmic/utils/gstreamer0.10-tools"), and whilst I'm not sure either, I think it's highly likely to be included in Ubuntu by default, especially considering totem uses the gstreamer backend by default.

Thanks, yep [this package list]("http://packages.ubuntu.com/lucid/ubuntu-desktop") verifies that gstreamer is installed by default.

The package gstreamer0.10-plugins-base-apps has the package you mentioned - gstreamer0.10-tools :)

Another app from the link in your first post works for .ogg too: playsound

---

