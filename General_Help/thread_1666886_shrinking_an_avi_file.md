---
title: "shrinking an avi file"
date: 2011-01-14
forum: General Help
---

### Post by hwttdz on 2011-01-14
I have an avi file that was recorded at a high school sporting event at not terribly high quality, but the 5 minute avi file (created with dd_rescue -A /path/to/cd /path/to/output.avi) is something like 250 Mb.  Which is far too large for a clip of this length and quality.  Any ideas on shrinking the file? (if I need to lift from the cd again that's fine).

---

### Post by ajgreeny on 2011-01-14
Probably **ffmpeg** is the best tool for something like that, but it is a command line tool.  Have a good search around about the best way to do it; it will probably be trial and error to get it right, but it should certainly do it for you.

If you want a GUI application winff is the app to look at.  I am not sure if it allows all the possible options of the command line tool, but again it should help you.

---

### Post by hansolo4949 on 2011-01-14
It sounds like you want some video compression software. You should easily be able to find some on the software center, or by googling it.

---

### Post by hansolo4949 on 2011-01-14
Double Post

---

### Post by hansolo4949 on 2011-01-14
It sounds like you want some video compression software. You should easily be able to find some on the software center, or by googling it.

---

### Post by pl@yer on 2011-01-14
You can use something like avidemux to encode the file.

---

