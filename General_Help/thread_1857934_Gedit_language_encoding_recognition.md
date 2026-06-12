---
title: "Gedit language encoding recognition"
date: 2011-10-11
forum: General Help
---

### Post by jazzon on 2011-10-11
had a document i recieved a few eeks ago that was utf-16 encoded.  When i opened it with gedit, it didnt recognize the enoding, so i had to add the encoding type.

Now it recognizes a bunch of documents as utf-16 that arent utf-16.

How can I undue this?

---

### Post by jazzon on 2011-10-11
Any ideas here folks?  Becoming a nuisance.

---

### Post by Vaphell on 2011-10-11
afaik gedit has a queue of encodings to try and the first one that allows to read the file is assumed to be the correct one. Move utf16 down the queue so other encodings are tried first or remove it entirely.

in gconf-editor
apps/gedit-2/preferences/encodings/auto_detected

for example for my work i need to edit tons of iso8859-2 files so my settings are: ISO-8859-2, UTF-8, CURRENT

---

### Post by jazzon on 2011-10-11
Thanks Vaph...that got it!

---

