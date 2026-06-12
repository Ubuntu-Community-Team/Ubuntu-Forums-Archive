---
title: "LibreOffice font error - Nimbus Sans L"
date: 2011-12-15
forum: General Help
---

### Post by etienne@Rofti on 2011-12-15
Dear all

As many of you might, I use LibreOffice 3.4.4 (on 32-bit Ubuntu 11.10) for most of my document and spreadsheet needs. I am also a graduate student writing my Masters thesis, and I use LibreOffice for it (...because I have to email my chapters as .doc's for feedback, though I would rather use LyX)

However, for inter-platform operability, and for the eventual printed product, I have made the font style for paragraphs and body "Times" (not Times New Roman, just Times) and for the headings, I typed in "Helvetica".

Usually, LibreOffice (and OpenOffice.org in the past) would substitute Nimbus Roman L and Sans L, respectively, for the fonts, and it would work really well. However, LibreOffice does not seem to want to see any other Nimbus Sans L font other than Condensed. Roman L works perfectly, but I cannot use the normal Nimbus Sans L, because when I use that font, the Condensed version is the one used, not Normal/Book/Roman.

So, the next logical step would be font substitution. I chose FreeSans to substitute Helvetica, but then LibreOffice took the metrics/width of Nimbus Sans L condensed again and applied it to FreeSans, so the letters are too close together.

I am at my wit's end. Does anyone know if there is a problem with LibreOffice or with Ubuntu? Why will it not just read and use the normal Nimbus Sans L, which is installed by default anyway?

Any help would be greatly appreciated.

Thank you.

---

### Post by BC59 on 2011-12-15
Some ideas:
You could install Google fonts and check if LibreOffice behaves better with them.
[http://www.webupd8.org/2011/01/automatically-install-all-google-web.html](http://www.webupd8.org/2011/01/automatically-install-all-google-web.html)

The text font rendering on LibreOffice has to do with the Cairo Graphics Rendering (don't ask me to help on this!)
[http://hackage.haskell.org/packages/archive/cairo/0.12.0/doc/html/Graphics-Rendering-Cairo.html](http://hackage.haskell.org/packages/archive/cairo/0.12.0/doc/html/Graphics-Rendering-Cairo.html)

Other solution would be installing the latest OpenOffice which I hear is getting slowly better than LibreOffice.

---

### Post by rng on 2011-12-15
I am having similar problem with powerpoint presentations as well. Files created in openoffice/libreoffice show altered fonts/sizes/format/layout when opened in windows powerpoint.

---

### Post by BC59 on 2011-12-15
> **rng said:**
> I am having similar problem with powerpoint presentations as well. Files created in openoffice/libreoffice show altered fonts/sizes/format/layout when opened in windows powerpoint.

I installed OOffice 3.4 on a WindowsXP virtual machine (because it's easier to install it on Win) and it's awesome. You can open a word file in 2 secs.
Now I'm trying to find how I can install it in Ubuntu, without messing the whole system removing LibreOffice. Another problem is that OOffice 3.4 lacks desktop integration on Ubuntu.

---

