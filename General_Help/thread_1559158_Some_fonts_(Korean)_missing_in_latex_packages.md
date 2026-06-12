---
title: "Some fonts (Korean) missing in latex packages"
date: 2010-08-23
forum: General Help
---

### Post by dasony on 2010-08-23
Hi,

I am trying to use CJK package to print out some Korean in mj font. 
(\begin{CJK}{UTF8}{mj})
It works fine in MacTex on my MacBook, but it gives me error on Ubuntu Lucid.

```

/usr/share/texmf/web2c/mktexnam: Could not map typeface abbreviation wm for uwmj5d.
/usr/share/texmf/web2c/mktexnam: Need to update /usr/share/texmf-texlive/fonts/map/fontname/special.map?
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input uwmj5d
This is METAFONT, Version 2.718281 (TeX Live 2009/Debian)


kpathsea: Running mktexmf uwmj5d
! I can't find file `uwmj5d'.
<*> ...:=ljfour; mag:=1; nonstopmode; input uwmj5d
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input uwmj5d
                                                  
Transcript written on mfput.log.
grep: uwmj5d.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input uwmj5d' failed to make uwmj5d.tfm.
kpathsea: Appending font creation commands to missfont.log.

! Font C70/mj/m/n/10/5d=uwmj5d at 10.0pt not loadable: Metric (TFM) file not fo
und.

```Compared to my Macbook, Ubuntu is missing some tfm and vf files for "uwmj" font.
It is in the regular texlive distribution: [http://m.tug.org/texmf-dist/fonts/tfm/uhc/](http://m.tug.org/texmf-dist/fonts/tfm/uhc/)
However it's not in any of Ubuntu package.

I have installed latex-cjk-all, texlive-fonts-recommended, texlive-fonts-extra.
I even ran getnonfreefonts just in case.

Any idea how I can install them?
Can I just download them all, dump them in, and run mktexlsr? 

Is this a bug in Ubuntu package or intended behaviour?

Thanks in advance.

---

