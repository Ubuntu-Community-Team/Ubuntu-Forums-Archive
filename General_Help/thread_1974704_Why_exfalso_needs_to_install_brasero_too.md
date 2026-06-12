---
title: "Why exfalso needs to install brasero too?"
date: 2012-05-06
forum: General Help
---

### Post by tanoloco on 2012-05-06
Hello,

I'm on a lubuntu 12.04 machine and would like to install exfalso

```

$ sudo apt-get install exfalso
... 
The following NEW packages will be installed:
  brasero brasero-cdrkit brasero-common dvd+rw-tools growisofs libart-2.0-2
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libbrasero-media3-1 libdee-1.0-4 libgee2 libgmime-2.6-0 libgnome2-0
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libidl-common libidl0
  libindicate-gtk3 libindicate5 liborbit2 libquvi-scripts libquvi7
  libtotem-plparser17 libunity9 python-cddb python-gconf python-gnome2
  python-indicate python-musicbrainz2 python-mutagen python-pyorbit
  quodlibet-plugins wodim
...

```

I don't want to install brasero (xfburn is enough for my needs) and I don't want to install all those packages for the gnome desktop.

Any idea why exfalso needs all this staff (and why brasero???) and how to avoid all this?

Thanks in advance

---

### Post by lazka on 2012-05-06
```
sudo apt-get --no-install-recommends install exfalso
```

There are (mostly) three types of dependencies:

**normal ones:** can't run without them
**recommends:** most users would like them (exfalso recommends quodlibet-plugins which recommends brasero since it includes a plugin for burning)
**suggests:** some users might like to install them

normal and recommends get installed by default. Use **--no-install-recommends** to just install what is really needed.

hth

(If there is any problem with exfalso, file a bug report at: [http://code.google.com/p/quodlibet/issues/entry](http://code.google.com/p/quodlibet/issues/entry) )

---

### Post by Dennis N on 2012-05-06
An alternate tag editor which doesn't depend on brasero would be tagtool.


Description pulled from *apt-cache show tagtool*:

> Description: Tool to tag and rename MP3 and Ogg Vorbis files. Audio Tag Tool is a program to manage the information fields in MP3 and Ogg Vorbis files (commonly called tags). Tag Tool can be used to edit tags one by one, but the most useful features are mass tag and mass rename. These are designed to tag or rename hundreds of files at once, in any desired format.


---

### Post by tanoloco on 2012-05-06
@lazka
Perfect, thanks a million!

@Dennis N
Thanks for the tip. I don't remember at the moment if I had a look at that one, I usually use exfalso in combination with easytag, but I'm always opened to new tools .. thus I'll give it a try for sure, thanks again.

:D

---

