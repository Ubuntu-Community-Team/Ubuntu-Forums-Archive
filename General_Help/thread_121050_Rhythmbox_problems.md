---
title: "Rhythmbox problems"
date: 2006-01-24
forum: General Help
---

### Post by Wolfbite on 2006-01-24
When I'm importing my mp3 folder to Rhythmbox, it only imports a few of the artists/albums while I get the error message: The following files couldn't be loaded: this file is not an audio stream. But the thousands of mp3's and oggs it can't load are indeed audio streams. I'm flabbergasted. :(

---

### Post by nik on 2006-01-24
You're probably missing some codecs. Try to follow the instructions about restricted formats in the wiki, or go for automatix, and try again.

---

### Post by doclivingston on 2006-01-24
[QUOTE=Wolfbite]When I'm importing my mp3 folder to Rhythmbox, it only imports a few of the artists/albums while I get the error message: The following files couldn't be loaded: this file is not an audio stream. But the thousands of mp3's and oggs it can't load are indeed audio streams. I'm flabbergasted. :([/QUOTE]

That error normally means that the gstreamer codec is missing, as Ubuntu doesn't have the mp3 codec installed out-of-the-box. It complaining about ogg files sound very odd.

If you have Totem-gstreamer installed (it is by default, unless you changed it to Totem-xine) can you try playing the tracks in that, and see if they work?

---

### Post by Wolfbite on 2006-01-24
[QUOTE=doclivingston]That error normally means that the gstreamer codec is missing, as Ubuntu doesn't have the mp3 codec installed out-of-the-box. It complaining about ogg files sound very odd.

If you have Totem-gstreamer installed (it is by default, unless you changed it to Totem-xine) can you try playing the tracks in that, and see if they work?[/QUOTE]

Hehe, I didn't notice until now that the oggs work fine, but it won't import mp3's. :D I'll see if I can work out this problem now. :)

---

### Post by Wolfbite on 2006-01-24
Phew, I managed to fix it now, by finding a guide that actually made it work, haha. Before that I did a lot of weird stuff in Terminal, so my Ubuntu is probably messed up, but hey, the mp3's are playing, baby! :D

Here's the guide I found that worked like a charm:

[https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

---

