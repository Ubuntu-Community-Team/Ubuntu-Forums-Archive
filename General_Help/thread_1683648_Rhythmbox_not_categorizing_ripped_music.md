---
title: "Rhythmbox not categorizing ripped music"
date: 2011-02-07
forum: General Help
---

### Post by Mad dog on 2011-02-07
Hi guys, this is very perplexing to me. I can rip songs from a cd in Rhythmbox and it will build all the folders with artist, album and songs in my Music folder, but when I go to Rhythmbox, everything is listed as unknown.

If I look at a single song and look at the properties, the last tab called Audio lists everything as unknown.

It seems like Rhythmbox is missing a step when it rips songs off a cd, like it is not applying tags? or something.

Does anyone know what might be causing this?

---

### Post by Mad dog on 2011-02-07
I tried uninstalling and reinstalling Rhythmbox and also did the same for libid3. It's still not working.

---

### Post by Mad dog on 2011-02-07
I tried Sound-Juicer and it does the same thing. So something is broken in my system. Something to do with applying tags to mp3 when they are ripped from CD.

---

### Post by Mad dog on 2011-02-07
SOLUTION:

I had to edit the Gnome Audio Profile for MP3s to add a line indicating which tagging system to use.

Instructions:

-Open Rhythm box
-Edit>Preferences>Music tab>
-where it shows Preferred format choose "edit"
-now choose mp3 and choose edit
-now go all the way to the end of the string that is the GStreamer pipeline
-it should have ! id3v2mux at the end
-if it does not, add that

This solved the issue for me.

---

