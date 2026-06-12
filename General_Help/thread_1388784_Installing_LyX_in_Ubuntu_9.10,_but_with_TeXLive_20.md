---
title: "Installing LyX in Ubuntu 9.10, but with TeXLive 2008 DVD"
date: 2010-01-23
forum: General Help
---

### Post by PortableHuman on 2010-01-23
Hi all,

I'm new on these forums (and to Linux generally); I'm not sure if this is the right place for this question. If not, I'd appreciate it if one of the mods could move it to where it belongs.

OK, so I've already install my TeX system on Ubuntu 9.10 by means of the TeXLive 2008 DVD. Now, I want to install LyX with

```
sudo apt-get install lyx
```It then asks me to install the following packages:

```
The following NEW packages will be installed:
  dvipdfmx dvipng lacheck latex-beamer latex-xcolor libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libboost-regex1.38.0 libboost-signals1.38.0 libt1-5
  lmodern lyx lyx-common pgf preview-latex-style prosper ps2eps psutils
  tex-common texlive-base texlive-base-bin texlive-base-bin-doc texlive-common
  texlive-doc-base texlive-extra-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-extra
  texlive-generic-recommended texlive-humanities texlive-humanities-doc
  texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-pictures texlive-pictures-doc
  texlive-pstricks texlive-pstricks-doc tipa ttf-lyx

```Note how a large number of texlive packages are to be downloaded and installed -- this is problematic with my limited monthly cap, but it also seems redundant given my already installed TeX system.

So, how can I install LyX without having to download packages I should already have. I suspect that the problem is that the repositories have TeXLive 2007, and I've installed 2008.

Does anyone know a way around this problem? Any help is greatly appreciated.

Regards,
PortableHuman

---

### Post by PortableHuman on 2010-01-23
OK, sorted this out by just compiling LyX from source. It handled everything else automatically, which is awesome. :D

---

