---
title: "Amarok help"
date: 2010-06-26
forum: General Help
---

### Post by Coltaaan on 2010-06-26
Hi, I just downloaded Amarok.I did so by going to the terminal and putting in:
-sudo apt-get install amarok

It appeared to work and everything, however I cant seem to get mp3's or the radio to work in it. I'm very new to Linux and Ubuntu, so some help would greatly be appreciated. Thanks!

---

### Post by jmszr on 2010-06-26
Coltaaan,

For mp3 playback install:

```
sudo apt-get install ubuntu-restricted-extras
```
According to Synaptic: Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

I don't know about the radio.

Edit: Make sure you have the Multiverse repository under Software Sources > Ubuntu Software checkmarked first.

---

