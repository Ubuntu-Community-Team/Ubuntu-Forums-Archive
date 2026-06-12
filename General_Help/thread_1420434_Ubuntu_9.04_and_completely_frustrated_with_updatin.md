---
title: "Ubuntu 9.04 and completely frustrated with updating to Picard 12.1"
date: 2010-03-03
forum: General Help
---

### Post by LinuxTAd on 2010-03-03
First off, I am staying with 9.04 for the time being. ;)

I have to uninstall Picard 11, done, and installed picard 12.1 I attempted to have my cake and eat it too, but both cannot co-exist.

**Some general readme info from install**
> Dependencies
------------

Before installing Picard, you need to have these libraries:

 * Python 2.5 or newer
   [http://python.org](http://python.org)
 
 * PyQt 4.1 with Qt 4.2 or newer
   [http://www.riverbankcomputing.co.uk/software/pyqt/intro](http://www.riverbankcomputing.co.uk/software/pyqt/intro)
   [http://www.trolltech.com/products/qt/](http://www.trolltech.com/products/qt/)

 * Mutagen 1.11 or newer
   [http://code.google.com/p/quodlibet/wiki/Development/Mutagen](http://code.google.com/p/quodlibet/wiki/Development/Mutagen)

 * libdiscid (optional)
   [http://musicbrainz.org/doc/libdiscid](http://musicbrainz.org/doc/libdiscid)

 * FFmpeg (optional)
   [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)

 * libofa (optional)
   [http://code.google.com/p/musicip-libofa/](http://code.google.com/p/musicip-libofa/)




**Python 2.5+** [COLOR="Lime"]Check![/COLOR]
**PyQt 4.1 with Qt 4.2 or newer**  [COLOR="lime"]Check![/COLOR]
**Mutagen 1.11 or newer**  [COLOR="lime"]Check![/COLOR]
**libdiscid**  [COLOR="lime"]Check![/COLOR] hmmm I have 0.1.0 and they are on .2.2...
**FFmpeg**  [COLOR="lime"]Check![/COLOR]
**libofa**  [COLOR="lime"]Check![/COLOR] Notes more version differences

**My build.cfg looks like this: **

```
[directshow]
libs = 
cflags = 

[libofa]
libs = -lofa -lfftw3 -lm
cflags = 

[avcodec]
libs = 
cflags = 

[build]
with-directshow = False
with-avcodec = False
with-libofa = True
```

and everything seems to start out well, until I attempt to perform a "scan" of some files.

> W: 3083736784 00:11:34 No decoders found! Fingerprinting will be disabled.

:-s

I am too tired tonight to track this down, I have seen also a few posts (one from a Mac) that look the same, but with all the installs out there there would be more I would think... Am I the last hold out on Jaunty lol :p

---

### Post by LinuxTAd on 2010-03-04
Ok,

I updated to the latest libdiscid from here:

[http://musicbrainz.org/doc/libdiscid](http://musicbrainz.org/doc/libdiscid)

tried to run picard via launcher, nothing...

Tried a reinstall, all went fine... tried to run again, nothing...

open terminal and typed picard,  behold!  :-k

```
$ picard
Traceback (most recent call last):
  File "/usr/local/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale', True)
  File "/usr/local/lib/python2.6/dist-packages/picard/tagger.py", line 63, in <module>
    from picard.formats import open as open_file
  File "/usr/local/lib/python2.6/dist-packages/picard/formats/__init__.py", line 51, in <module>
    from mutagen import _util
ImportError: No module named mutagen

```

I had it installed and updated I had checked last night!... I goto Synaptic and type in mutagen, the only thing that comes up is python-mutagen (1.14-2 Jaunty). Knowing that often times Linux ask for things in a very non-descriptive way I am thinking I had better install it ;). I am also reminded once again at the simple inability to just copy and paste information from package>properties>Versions or from a few other areas there... :rolleyes:

Installed, and again in terminal... W: 3085686480 23:10:33 No decoders found! Fingerprinting will be disabled.

Yeah!!!:P Fail :-({|=
](*,)

Log into Windows XP SP3 on my laptop... Download latest Picard, install, run. It works. 
:evil:

I have been bested by windows!

not yet, I will try some more!

---

