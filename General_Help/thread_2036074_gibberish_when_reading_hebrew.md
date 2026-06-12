---
title: "gibberish when reading hebrew"
date: 2012-08-01
forum: General Help
---

### Post by mich3lam on 2012-08-01
hey, everything is in gibberish when i open a file in geditor... i instralled the language support and still.. any idea how i can fix that? it's important since mencoder reads .srt files in gibberish too and i want to use hebrew subtitles... ty

edit: i just found out that when i make a new text document and write and hebrew and save it, i can read it.
those .srt files i see in gibberish are not corrupted, since i can play them using VL C when choosing the encoding in it. but how do it for the text files?

---

### Post by rich1842 on 2012-08-01
convmv -r --notest -f windows-1255 -t UTF-8 *

and

convmv -r --notest -f windows-1252 -t UTF-8 *

(1252 is Latin, 1255 is Hebrew)

You could try these...

these will update the character sets available to you hopefully

---

### Post by Vaphell on 2012-08-01
if you want to see the content, you need to open the file with a desired encoding. in case of gedit there should be a dropdown in Open file dialog, also in gedit preferences you can set the order of encodings tried to open the file, you need to use gconf-editor/dconf-editor depending on the ubuntu version.

---

