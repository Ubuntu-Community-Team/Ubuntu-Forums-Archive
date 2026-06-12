---
title: "MP3 tagger request"
date: 2010-08-14
forum: General Help
---

### Post by Bent Axle on 2010-08-14
Hi All

I'm a new Gnome user... I've used KDE for about 8 years. I'm using Lucid.

I'm looking for a decent mp3 tagger that displays ALL of the extended tags that an MP3 file might have in it. All of the gnome taggers in the repos only display (and give you the ability to edit) the top 12 or so tag fields. Any extended tags or user created tags are hidden and cannot be edited.

Kid3 does this with ease however this is a KDE app and looks out of place on the desktop. The closest I've found is Puddletag from some ppa somewhere, however it crashes with some dependency failure...

Any and all comments welcome.

BA

---

### Post by ufleisch on 2010-08-15
You can use [kid3-qt]("http://packages.ubuntu.com/lucid/kid3-qt"). It does not use any KDE libraries, just Qt, so it should not integrate too bad into your Gnome desktop.

---

### Post by Bent Axle on 2010-08-15
Hi ufleisch

That's brilliant. Thank you so much for the solution. That looks much better than the KDE version.

I'm amazed though that there is not a id3 tagger that does this normally in Gnome.

BA

---

### Post by egd on 2010-08-27
> **Bent Axle said:**
> The closest I've found is Puddletag from some ppa somewhere, however it crashes with some dependency failure...Download the latest puddletag from [https://sourceforge.net/projects/puddletag/files/latest](https://sourceforge.net/projects/puddletag/files/latest) and use the following to install the dependencies:```
**sudo aptitude install python-qt4 python-pyparsing python-mutagen python-configobj python-musicbrainz2 python-imaging**
```puddletag's homepage is a useful reference point: [http://puddletag.sourceforge.net/index.html](http://puddletag.sourceforge.net/index.html)

---

### Post by elliotn on 2010-08-27
Try easy tag editor or mp3info they are good also

---

### Post by FrankVdb on 2010-08-28
I use EasyTag. 

It tags. Easy. :P

---

