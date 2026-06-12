---
title: "No video"
date: 2010-02-14
forum: General Help
---

### Post by laloruelas on 2010-02-14
I Cant play videos in totem, i only get the sound from it, it is really annoying, what can i do, i have already reinstalled totem, and all codecs. help.

---

### Post by lidex on 2010-02-14
Since I'm not Kreskin ;) I will simply point you to this exhaustive guide:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by laloruelas on 2010-02-14
tried the link. . . . . .did not work, i'm about to cry.

---

### Post by sandyd on 2010-02-14
try vlc.

p.s. did you install video drivers?

---

### Post by laloruelas on 2010-02-14
i did install video drives, for my nvidia card, flash video works but wmv, and quicktime only have sound

---

### Post by lidex on 2010-02-14
> **laloruelas said:**
> i did install video drives, for my nvidia card, flash video works but wmv, and quicktime only have sound

What about mpg and avi? You haven't tried vlc, as suggested, or mplayer?

---

### Post by laloruelas on 2010-02-14
i installed restricted extras, and video works in mplayer, but i don know how to get mozilla to use it to open videos and to show video objects

---

### Post by lidex on 2010-02-14
So you're referring to streaming video? Your initial post wasn't very clear then. What browser are you using?

---

### Post by mionescu on 2010-02-14
You can install mozilla-mplayer and then firefox should use mplayer for videos.

---

### Post by laloruelas on 2010-02-15
neither streaming, nor playing files has video, only sound

---

### Post by lidex on 2010-02-15
What browser are you using?
Try this in a terminal:
```
sudo apt-get install gecko-mediaplayer
```

"applications/accessories/terminal"

---

### Post by laloruelas on 2010-02-15
You fixed the streaming video problem with the command, but on my desktop, with totem movie player, i still only get sound with wmv and mov files. i am using firefox web browser

---

### Post by lidex on 2010-02-15
Terminal commands;
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras libxine1-ffmpeg
sudo aptitude install libdvdread3 libdvdnav4 libdvdcss2 regionset gnome-mplayer
sudo aptitude install non-free-codecs w32codecs
sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-plugins-good
sudo aptitude install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse


```

---

### Post by lidex on 2010-02-15
If that doesn't get it working, I don't know what to tell you. BTW, you stated mplayer does the job - what's wrong with that? If it's an interface issue, the smplayer front end is pretty sweet.

---

