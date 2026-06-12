---
title: "embedded fonts in PDFs"
date: 2012-03-18
forum: General Help
---

### Post by frozenthrone on 2012-03-18
Hello,

I've got a PDF file including embedded fonts. Neither Okular nor Evince can display any charakter using these embedded fonts. Where the writing should be displayed, there is just empty blank space, so both of them are not even trying zu replace them by included system fonts.

EVEN (!!) Adobe Reader for Linux itself is not able to display characters using these special fonts correctly. Instead, it just shows an error message that they cannot be loaded and leaves an empty space where text should be standing.

After hours of googling I found out that Chrome has got an integrated PDF-viewer. I have chosen it for the default application to display PDFs - an it displays them correctly. Althought is not the best solution, it is much better than nothing.

On Windows this PDF is displayed correctly using Adobe Reader.

BUT: I am wondering. Is there really absolutely no way to fulfill the 1.7-standart? Why is it nearly impossible and so frustrating just to open and print out a simple PDF-file uncluding embedded fonts?

frozenthrone

---

### Post by Rodney9 on 2012-03-18
I not sure but installing fonts may help and from what I see on the net cm super and/or lm fonts may be needed.

> 
sudo apt-get install lmodern cm-super
 

TeX font package (full version) with CM (EC) in Type1 in T1, T2*, TS1, X2 enc

This package ships the full set of cm-super fonts, for a minimal variant
 install cm-super-minimal.

The **CM-Super** package contains Type 1 fonts converted from METAFONT
fonts and covers entire EC/TC, EC Concrete, EC Bright and LH fonts
(Computer Modern font families). All European and Cyrillic writings
are covered. Each Type 1 font program contains ALL glyphs from the
following standard LaTeX font encodings: T1, TS1, T2A, T2B, T2C, X2,
and also Adobe StandardEncoding (585 glyphs per non-SC font and 468
glyphs per SC font), and could be reencoded to any of these encodings
using standard dvips or pdftex facilities (the corresponding support
files are also included).

The **Latin Modern **fonts, also known as "lm fonts", are a set of
 scalable fonts in PostScript Type 1 and OpenType formats. They are
based on the PostScript Type 1 version of the Computer Modern fonts
and contain many additional characters (mostly accented ones).

The Latin Modern fonts were generated using MetaType1, a program
based on MetaPost for generating PostScript Type 1 fonts
([ftp://bop.eps.gda.pl/pub/metatype1/](ftp://bop.eps.gda.pl/pub/metatype1/)). Their size is reasonable and
they are usually considered to be of good quality (compared to
cm-super, for instance; however, cm-super contains font families
that have no equivalent in this package; additionally, there are
character sets that are supported by cm-super and not by the Latin
Modern fonts).

The fonts are setup for use with the TeX typesetting system. They
are also registered with defoma, which makes them available to other
applications such as Ghostscript and Fontconfig. Finally, they are
made available to the core X11 fonts system, which makes it possible
to use them in any X application.

Rodney

---

