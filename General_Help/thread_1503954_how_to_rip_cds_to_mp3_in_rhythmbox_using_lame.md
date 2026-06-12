---
title: "how to rip cds to mp3 in rhythmbox using lame?"
date: 2010-06-07
forum: General Help
---

### Post by princeofnam on 2010-06-07
i've downloaded LAME, but I don't know exactly how to use it in order to begin ripping CDS to the mp3 format.

---

### Post by dino99 on 2010-06-07
[http://wiki.audacityteam.org/index.php?title=Lame_Installation](http://wiki.audacityteam.org/index.php?title=Lame_Installation)

---

### Post by oldos2er on 2010-06-07
In Rhythmbox, click the menus Edit, Preferences, Music tab, change your preferred format to mp3. Then with a CD in the drive, click Music, Duplicate Audio CD.

Edit: Or if you just want to rip tracks to your hard drive, click the 'Copy tracks to the library' icon.

---

### Post by princeofnam on 2010-06-07
oh sorry. i forgot to mention i already installed it. i just don't know why rhythmbox hasn't allowed me the option to rip to mp3 yet

---

### Post by princeofnam on 2010-06-07
i see mp3 under profiles but not under the preferred formats drop down list

---

### Post by princeofnam on 2010-06-07
anyone?

---

### Post by oldos2er on 2010-06-07
I don't see "profiles" anywhere in Rhythmbox. Can you provide a screenshot?

---

### Post by princeofnam on 2010-06-07
here they are

---

### Post by oldos2er on 2010-06-08
Thanks for providing those pics. Have you restarted Rhythmbox or rebooted since installing libmp3lame0? Have you installed ubuntu-restricted-extras?

---

### Post by growingneeds on 2010-11-02
Hi. From Synaptic, simply install the meta-package "gstreamer0.10-plugins-ugly-multiverse". This will enable the selection of mp3 from the preferred format list in RhythmBox. Remember it has to be the multiverse variant. This will enable the selection of libmp3lame0 and libx264-85.

I have used RipperX previously, but it always crashes after ripping. In addition, the id3 tags are messed up from track 10 onwards. As such, I have returned to RhythmBox. Remember, choose the multiverse variant.

---

