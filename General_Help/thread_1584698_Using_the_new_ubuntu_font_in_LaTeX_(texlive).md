---
title: "Using the new ubuntu font in LaTeX (texlive)"
date: 2010-09-29
forum: General Help
---

### Post by jon.reeve on 2010-09-29
I really like the new Ubuntu font, and I'd love to use it in documents that I make with LaTeX. Anyone have any ideas about how to import new fonts into texlive?

---

### Post by Tibuda on 2010-09-29
I didn't knew it was possible to use TrueType fonts in LaTeX. Here's some instructions I have found:
[http://fachschaft.physik.uni-greifswald.de/~stitch/ttf.html](http://fachschaft.physik.uni-greifswald.de/~stitch/ttf.html)
[http://www.radamir.com/tex/ttf-tex.htm](http://www.radamir.com/tex/ttf-tex.htm)

---

### Post by eltama on 2010-10-01
Thanks for the links, I will try them.
I'm starting to write my PhD thesis and I would like to use Ubuntu's font on the titles!

---

### Post by eltama on 2010-10-01
I got a test working, see the attachment.

There is only one annoying problem. The intermediate dvi cannot be read by evince, but what it worse, when nautilus-thumbnailer tries to create a thumbnail, it starts using all the cpu and does not finish. You have to kill the process.
So be sure to remove the dvi before going to nautilus (a build script would be useful).

---

### Post by jon.reeve on 2010-10-01
That's great, thanks for the files! I'm going to get a lot of use out of this.

---

### Post by roggenschrotbrot on 2010-10-01
are kerning and ligatures still working as supposed this way?

---

### Post by eltama on 2010-10-04
> **roggenschrotbrot said:**
> are kerning and ligatures still working as supposed this way?

I made a test, see the attached image.
I'm not an expert but I'd say that there is no kerning and ligatures, but that it still looks fine.

Update: after looking at it more closely I think that there are ligatures. Look how in fjörd the j goes under the f.

---

### Post by roggenschrotbrot on 2010-10-04
thank you very much. i guess i'll give it a try to see how it looks with a larger text in small print.

the unicode ligature characters of the font itself look this way aswell, so these might be used for ligatures in latex. i'll test it with a font offering more obvious ligatures later.

edit: the font seems to work quite well with larger texts.

---

### Post by jordilin on 2010-10-05
> **Tibuda said:**
> I didn't knew it was possible to use TrueType fonts in LaTeX. Here's some instructions I have found:
[http://fachschaft.physik.uni-greifswald.de/~stitch/ttf.html](http://fachschaft.physik.uni-greifswald.de/~stitch/ttf.html)
[http://www.radamir.com/tex/ttf-tex.htm](http://www.radamir.com/tex/ttf-tex.htm)

You can use xetex which is very straightforward.

---

### Post by eltama on 2010-10-05
> **roggenschrotbrot said:**
> thank you very much. i guess i'll give it a try to see how it looks with a larger text in small print.

the unicode ligature characters of the font itself look this way aswell, so these might be used for ligatures in latex. i'll test it with a font offering more obvious ligatures later.

edit: the font seems to work quite well with larger texts.

Great!

---

### Post by eltama on 2010-10-05
> **jordilin said:**
> You can use xetex which is very straightforward.

I had never used xetex before. I tried the example from [http://en.wikipedia.org/wiki/XeTeX]("http://en.wikipedia.org/wiki/XeTeX") that uses the font Linux Libertine and changed it to the Ubuntu font.

I works fine (except for some things that do not work because the font is still not complete).

---

### Post by ratcat on 2010-10-09
My 10.10 has the Sans font. Where do I get the new Ubuntu font I read about ? The font display in Ubuntu is excellent.

---

### Post by eltama on 2010-10-10
> **ratcat said:**
> My 10.10 has the Sans font. Where do I get the new Ubuntu font I read about ? The font display in Ubuntu is excellent.

Ubuntu's font is preinstalled in 10.10 and it is used in some of the default configurations. But if you had been using the alphas I think it is not used by default. But you can select it in System > Preferences > Appearance > Fonts. The font is called Ubuntu.

There is also a ppa for older systems, but if you are using 10.10 you shouldn't need it.

---

### Post by HandleWithCare on 2010-11-13
Maybe I missed some steps, but I can't get this to work. Do I need to place some fontfiles at a certain place?

These are the errors I get when I try to run ubuntu.tex (from the zipfile some posts back):

```

Process started

kpathsea: Invalid fontname `[lmroman10-regular]:mapping=tex-text', contains '['

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Appending font creation commands to missfont.log. kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu/B

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation B for B. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input B

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf B

! I can't find file `B'. <*> \mode:=ljfour; mag:=1; nonstopmode; input B Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input B Transcript written on mfput.log.

grep: B.log

: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input B' failed to make B.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu/I

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation I for I. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input I

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf I

! I can't find file `I'. <*> \mode:=ljfour; mag:=1; nonstopmode; input I Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input I Transcript written on mfput.log.

grep: I.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input I' failed to make I.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log

: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu/BI

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation B for BI. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input BI

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf BI

! I can't find file `BI'. <*> \mode:=ljfour; mag:=1; nonstopmode; input BI Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input BI Transcript written on mfput.log.

grep: BI.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input BI' failed to make BI.tfm. kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':'

kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':'

kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':' kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':' kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':'

kpathsea: Invalid fontname `Ubuntu:mapping=tex-text;', contains ':' kpathsea: Invalid fontname `Ubuntu Italic', contains ' '

kpathsea: Invalid fontname `Ubuntu Italic', contains ' '

kpathsea: Invalid fontname `Ubuntu Italic', contains ' '

kpathsea: Invalid fontname `Ubuntu Italic', contains ' '

kpathsea: Invalid fontname `Ubuntu Italic/B', contains ' ' kpathsea: Invalid fontname `Ubuntu Italic', contains ' ' kpathsea: Invalid fontname `Ubuntu Italic/I', contains ' ' kpathsea: Invalid fontname `Ubuntu Italic', contains ' ' kpathsea: Invalid fontname `Ubuntu Italic/BI', contains ' '

kpathsea: Invalid fontname `Ubuntu Italic:', contains ' ' kpathsea: Invalid fontname `Ubuntu Italic:', contains ' ' kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu/B

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation B for B. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input B

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf B

! I can't find file `B'. <*> \mode:=ljfour; mag:=1; nonstopmode; input B Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input B Transcript written on mfput.log.

grep: B.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input B' failed to make B.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu/I

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation I for I. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input I

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf I

! I can't find file `I'. <*> \mode:=ljfour; mag:=1; nonstopmode; input I Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input I Transcript written on mfput.log.

grep: I.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input I' failed to make I.tfm. kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm. kpathsea: Running mktextfm Ubuntu/BI

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation B for BI. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input BI

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf BI

! I can't find file `BI'. <*> \mode:=ljfour; mag:=1; nonstopmode; input BI Please type another input file name ! Emergency stop. <*> \mode:=ljfour; mag:=1; nonstopmode; input BI Transcript written on mfput.log.

grep: BI.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input BI' failed to make BI.tfm.

kpathsea: Invalid fontname `Ubuntu:', contains ':' kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.

kpathsea: Running mktextfm Ubuntu

/usr/share/texmf/web2c/mktexnam: Could not map source abbreviation U for Ubuntu. /usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?

mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu

This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)

kpathsea: Running mktexmf Ubuntu

! I can't find file `Ubuntu'. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Please type another input file name ! Emergency stop. <*> ...:=ljfour; mag:=1; nonstopmode; input Ubuntu Transcript written on mfput.log.

grep: Ubuntu.log: No such file or directory

mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input Ubuntu' failed to make Ubuntu.tfm.


```

---

### Post by Sven03149 on 2011-05-16
I've made a bundle of the Ubuntu Font Family for LaTeX2e. You can download it from github:

[https://github.com/tzwenn/ubuntu-latex-fonts]("https://github.com/tzwenn/ubuntu-latex-fonts")

For installation just run:

```
sudo make install

```

and then type \usepackage{ubuntu} in your LaTeX file.

---

