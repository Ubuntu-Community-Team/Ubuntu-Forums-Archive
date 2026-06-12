---
title: "Help With Mplayer please"
date: 2006-02-11
forum: General Help
---

### Post by BitTorrentBuddha on 2006-02-11
I just tried watching an wmv format video. Mplayer works great, but whenever I set it to full screen [with zoom changed to yes in mplayer.conf] the video slows down while the audio carries on at full speed. Alternatively, if I could get sound working properly for Totem for the wmv extensions, that would be much better as I feel mplayer is an inferior product anyways.

---

### Post by nalmeth on 2006-02-11
whats wrong with the audio in totem for you?

---

### Post by BitTorrentBuddha on 2006-02-11
it won't play audio for *.wmv

---

### Post by nalmeth on 2006-02-11
I like totem better aswell, though it has its shortcomings. I don't know much about the internals of these apps, so all I can think of is to make sure you have all the restricted audio and video formats installed with automatix, or whichever way you know best. Sorry, and good luck

---

### Post by dcstar on 2006-02-11
[QUOTE=BitTorrentBuddha]I just tried watching an wmv format video. Mplayer works great, but whenever I set it to full screen [with zoom changed to yes in mplayer.conf] the video slows down while the audio carries on at full speed. Alternatively, if I could get sound working properly for Totem for the wmv extensions, that would be much better as I feel mplayer is an inferior product anyways.[/QUOTE]
Do you have "Direct Rendering" working on your video card?, check with:

glxinfo

Also, Totem using xine and the w32codecs should play just about all formats ok.

---

### Post by BitTorrentBuddha on 2006-02-11
```
...
direct rendering: No
...
```
nope... but all I have is onboard video, is there a way to fix this?

---

### Post by BitTorrentBuddha on 2006-02-11
bump, how can I fix my direct rendering??

---

### Post by dcstar on 2006-02-11
[QUOTE=BitTorrentBuddha]```
...
direct rendering: No
...
```
nope... but all I have is onboard video, is there a way to fix this?[/QUOTE]
It depends on your video hardware, do a forum search for it and see if there is a HOWTO available.

My onboard VIA Unichrome video is now working with Direct Rendering (Hardware Acceleration), and it works a hell of a lot faster than without it.....         :D

---

### Post by BitTorrentBuddha on 2006-02-11
no, it's not a laggy slow-down, it's more of a methodic slowdown like it's going at half-speed

---

### Post by BitTorrentBuddha on 2006-02-11
ok, it's more a fractured sound when trying to play the wmv's [the IT crowd] and i hear a burst of sound once every fifteen or so seconds that lasts about half a second... I have installed and reinstalled the codecs off automatix and then an additional time manually... :(
Addtitionally, I thought the following lines of output when running in terminal seemed peculiar
```
(totem:13884): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:13884): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
```

---

### Post by BitTorrentBuddha on 2006-02-11
bump, anybody know what those errors mean ^^?

---

### Post by BitTorrentBuddha on 2006-02-12
bump :(

---

