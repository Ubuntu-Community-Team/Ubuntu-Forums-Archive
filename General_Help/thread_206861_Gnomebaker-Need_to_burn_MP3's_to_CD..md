---
title: "Gnomebaker-Need to burn MP3's to CD."
date: 2006-06-30
forum: General Help
---

### Post by zenwhen on 2006-06-30
I need to know what package needs to be installed in order to allow Gnomebaker to burn a set of MP3's to CD.

I have attached my current error. Thanks for any help.

---

### Post by woedend on 2006-06-30
gnomebaker uses gstreamer.  I THINK the version with dapper uses gstreamer 0.8.
Open synaptic, search for gstreamer, and install the appropriate 0.8 plugins.  I would give you the exact package name but don't have it in front of me...if you need me to find out let me know.
HTH

PS - on another note there is a deb floating around on these boards someplace of someone who compiled a new cvs version of gnomebaker which uses gstreamer-0.10

---

### Post by Donnut on 2006-06-30
Sort of a related question, will K3B burn mp3s to CD?

---

### Post by woedend on 2006-06-30
yes.  I think its separated into a package called k3b-mp3 (it used to be at least).
k3b is much better for this in that you can burn on the fly(ie, decode while burning, whereas gnome baker decodes all of the songs, then burns).

---

### Post by zenwhen on 2006-06-30
[QUOTE=woedend]gnomebaker uses gstreamer.  I THINK the version with dapper uses gstreamer 0.8.
Open synaptic, search for gstreamer, and install the appropriate 0.8 plugins.  I would give you the exact package name but don't have it in front of me...if you need me to find out let me know.
HTH

PS - on another note there is a deb floating around on these boards someplace of someone who compiled a new cvs version of gnomebaker which uses gstreamer-0.10[/QUOTE]
That did it. Thanks.

---

