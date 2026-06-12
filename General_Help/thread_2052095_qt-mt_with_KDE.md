---
title: "qt-mt with KDE?"
date: 2012-09-02
forum: General Help
---

### Post by jpharford on 2012-09-02
I'm trying to install tiemu (I've bought four ti-89 titaniums at $250+ each, so I feel okay doing this).  The snag is interesting...

I use the guide at the URL below to install KDE:

[http://techbase.kde.org/Getting_Started/Build/Distributions/Debian](http://techbase.kde.org/Getting_Started/Build/Distributions/Debian)

This gets rid of the configure complaints about KDE headers, BTW (I've seen an abundance of threads about that with solutions that don't work).  Small problem: It removed libqt3-mt-dev!  So, I'm left with "(library qt-mt) not found."  

Installing libqt3-mt-dev removed KDE headers.  'Round and 'round we go.

Can Qt not coexist with KDE?  Do these packages not get along?  They seem to have such a great history together!  I bet it's the in laws...

---

### Post by mastablasta on 2012-09-02
you do realise that Ubuntu has a newer KDE? 4.8 or something. you can install it from software center or oyu can simply install kubuntu-desktop for full kde desktop.

is tiemu still supported/developed? it could be that it is using some outdated libraries. pictures on their site are showing KDE3 or 2.
i would first search in synaptic to see if it can be installed from there.

---

### Post by spjackson on 2012-09-02
Qt 4 was released 7 years ago and Qt 3 reached "end of life" 5 years ago. Do you really still need to use it?

I'm afraid that I don't know if you can install Qt3 on a recent KDE.

---

### Post by jpharford on 2012-09-02
I don't need kubuntu, but just the KDE headers and Qt 3.0.2 to configure the make file for tiemu.  It's an old emulator; development was more or less abandoned after it was completed.

All I need is a 3d graphing calculator, so maybe I should poke around to see if WebGL can be made to work.

edit: Looks like Chrome for ubuntu may have it.
edit2: Yep!  Google's graph function works.

---

### Post by mastablasta on 2012-09-03
Porteus distribution uses Trinity (KDE3 fork): [http://distrowatch.com/table.php?distribution=porteus](http://distrowatch.com/table.php?distribution=porteus)
 
otherwise old libraries could maybe be found in synaptics.
 
but if you found a better 3D graph then use it. i used to use one that was preety good and made for DOS at the time. i neede it to caclula and show the forumals porpperly. i was still using it with Win98 and XP... i think it was called derive or something.

---

