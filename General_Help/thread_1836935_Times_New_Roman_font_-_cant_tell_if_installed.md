---
title: "Times New Roman font - cant tell if installed"
date: 2011-08-31
forum: General Help
---

### Post by u-noob-tu on 2011-08-31
this might sound like a silly issue but i cant tell if i have the Times New Roman font installed. I searched the software center for it and i seem to have the installer package, but in LibreOfiice i cant find it in the font selector. however i have a document that has the Times New Roman font and it says so in the font box, but when i make a new document i cant find it. the only reason i care is for compatibility with Microsoft Office (only one in my family that uses Ubuntu). How can i tell if its installed?

---

### Post by IWantFroyo on 2011-08-31
I think Sans Serif **is** Times New Roman. If not, you might want to type "ttf" in Synaptic and look through the different fonts.

---

### Post by lynrock on 2011-09-01
No, san serif is not Times New Roman (which is serifed).
Liberation Serif is a good substitute installed by default, otherwise you need to install the package ttf-mscorefonts-installer (which will then download the fonts).
In LibreOffice the font that shows up in the fontbox indicates which font is set for that particular imported document, even if the font isn't installed to display it.

---

### Post by garvinrick4 on 2011-09-01
Package: ttf-mscorefonts-installer       
State: installed
Automatically installed: no
Version: 3.3ubuntu3
Priority: optional
Section: multiverse/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 221 k
Depends: wget, cabextract, xfonts-utils, defoma, debconf (>= 0.5) | debconf-2.0
Recommends: ttf-liberation, x-ttcidfont-conf
Conflicts: msttcorefonts (< 2.6)
Replaces: msttcorefonts (< 2.6)
Provides: msttcorefonts
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type Core
 Fonts for the Web including: 
 
  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings
 
 You will need an Internet connection to download these fonts if you don't
 already have them. 
 
 NOTE: the package ttf-liberation contains free variants of the Times, Arial
 and Courier fonts. It's better to use those instead unless you specifically
 need one of the other fonts from this package.

---

### Post by u-noob-tu on 2011-09-01
i do have the ttf-mscorefonts-installer package installed, but the times new roman font is not visible in the font selection dialog. its just not there.

---

### Post by dino99 on 2011-09-01
[http://ubuntuforums.org/showthread.php?t=72007](http://ubuntuforums.org/showthread.php?t=72007)

[http://manpages.ubuntu.com/manpages/natty/en/man1/defoma.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/defoma.1.html)

---

### Post by u-noob-tu on 2011-09-01
i found the problem. somehow, during the installation of mscorefonts, i guess i refused the license agreement by mistake. i discovered this by looking at the first link provided by dino99. it said to look in usr/share/fonts/. there i found msttcorefonts folder, and inside was a single text file called "license". it said that the license had been refused and to reinstall. fixed the problem immediately. SOLVED!

---

