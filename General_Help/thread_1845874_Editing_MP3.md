---
title: "Editing MP3"
date: 2011-09-17
forum: General Help
---

### Post by Kaizoku001 on 2011-09-17
I need to edit a mp3 file and wanted to know what my options were.

I basicly would need to cut the first part of the song and save it in a separate file.

What software should I use?

---

### Post by tgalati4 on 2011-09-17
apt-cache search sox

sudo apt-get install sox libsox-fmt-all

man sox

sox crappy_sound_file.mp3 first_twenty_seconds_removed.mp3 trim 0 20

---

### Post by GWBouge on 2011-09-17
Audacity is a nice little tool for simple stuff.  You can find it in the Software Center, or just 'sudo apt-get install audacity'

Open your mp3 file in Audacity, select the section you want to cut, goto Edit -> Trim, save the new file.

---

### Post by Kaizoku001 on 2011-09-17
> **GWBouge said:**
> Audacity is a nice little tool for simple stuff.  You can find it in the Software Center, or just 'sudo apt-get install audacity'

Open your mp3 file in Audacity, select the section you want to cut, goto Edit -> Trim, save the new file.
Thanks!
Just what I needed.

@tgalati4
Also Thanks.
But I went with The GUI

---

### Post by tgalati4 on 2011-09-17
Audacity converts to WAV, edits the file, then converts back to mp3, so you may lose some quality.

---

### Post by Kaizoku001 on 2011-09-18
> **tgalati4 said:**
> Audacity converts to WAV, edits the file, then converts back to mp3, so you may lose some quality.
thanks for the heads up.
For the stuff I need now, quality isn't an issue thought.

Thanks

---

