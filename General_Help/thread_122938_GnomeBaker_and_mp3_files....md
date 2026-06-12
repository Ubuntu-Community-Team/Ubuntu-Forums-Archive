---
title: "GnomeBaker and mp3 files..."
date: 2006-01-28
forum: General Help
---

### Post by Elrohir on 2006-01-28
hi all! how you all hanging? got a question... last night I was trying to burn an audio CD... source files were .mp3 and when I tried to add the files in the list for burning, GnomeBaker send me an error message saying some plugins are missing... anyone had this error? what plugins do I need? where to find them?

TIA

---

### Post by kwaanens on 2006-01-28
[QUOTE=Elrohir]GnomeBaker send me an error message saying some plugins are missing...[/QUOTE]

The exact error message will  probably be needed if you want some help.

- Ketil

---

### Post by Elrohir on 2006-01-28
it says: ```
The plugin to handle a file of type audio/mpeg is not installed
```any ideas?

---

### Post by hav0x on 2006-01-28
sudo apt-get install serpentine gstreamer0.8-plugins gstreamer0.8-plugins-multiverse

edit: forgot ze plugins

---

### Post by kingsidy on 2006-01-28
install lame: sudo apt-get install lame
gstreamer0.8 lame search for this in synaptic
gstreamer0.8 plugins look for this in synaptic as well
better yet used automatic and install audio codecs

---

### Post by Elrohir on 2006-01-29
thanx! that was it...\\:D/

---

