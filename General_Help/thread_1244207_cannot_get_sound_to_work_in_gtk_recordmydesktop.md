---
title: "cannot get sound to work in gtk recordmydesktop"
date: 2009-08-19
forum: General Help
---

### Post by Achilles124 on 2009-08-19
Gtk recordmydesktop doesn't record any sound. 

This is what the terminal shows: [http://i304.photobucket.com/albums/nn177/Ptolemeus/Intelcard.png]("http://i304.photobucket.com/albums/nn177/Ptolemeus/Intelcard.png")

So I typed: hw:0,0 in the preferences in recordmydesktop.

I also checked my Alsamixer: [http://i304.photobucket.com/albums/nn177/Ptolemeus/Alsamixer.png]("http://i304.photobucket.com/albums/nn177/Ptolemeus/Alsamixer.png")

I am doing something wrong here, but I really don't know what.

---

### Post by Achilles124 on 2009-08-28
Got it to work by plugging in my microphone and changing the sound configuration in: hw 0,2.

---

### Post by rmcellig on 2009-09-08
How do you go about changing the sound configuration?

---

