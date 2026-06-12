---
title: "Problem with QT4 and MuseScore"
date: 2006-05-22
forum: General Help
---

### Post by silverklyph on 2006-05-22
Okay, I'm running Ubuntu, Breezy Badger on a Dell Inspiron 6000.

  I'm trying to install a program called MuseScore, it's a music notation editor that requires at least version 4.0.1 of QT, a c++ GUI library.  I'm using v4.1.3 because it was the easiest to find on the Trolltech website.

  I ran "./configure", "make", and "sudo make install", and set QTDIR to the default installation directory, where QT was installed.

  When I run ./configure in the musescore directory, it gets up to checking for QT and gives me something like this:

  Checking for QTDIR: yes
  Checking for includes: yes
  Checking for libs: no
  Checking for moc : yes
  Checking for <something else>: yes

Then it says that I need version >= 4.0.1 of QT and tells me to check config.log for more information.

  Checking config.log tells me that it cannot find sharedobject libQtCore.so.4, so off i go to $QTDIR/lib

  Upon inspection, libQtCore.so.4 is definitely there, and it's a link to an actual file libQtCore.so.4.1.3.

  Anyone know why it can't find it?

---

