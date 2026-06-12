---
title: "Installed texlive-full but can't find it"
date: 2010-08-10
forum: General Help
---

### Post by Lummy on 2010-08-10
i've just installed the texlive-full package from the universal respository using synaptic package manager. I cannot for the life of me figure out where texlive is on my system though! Any thoughts?

---

### Post by procras on 2010-08-10
Find installed files with locate

$ locate texlive |head -20
/etc/texmf/fmt.d/10texlive-base.cnf
/etc/texmf/fmt.d/10texlive-base.cnfpre-edit
/etc/texmf/fmt.d/10texlive-latex-base.cnf
/etc/texmf/hyphen.d/09texlive-base.cnf
/etc/texmf/language.d/09texlive-base.cnf
/etc/texmf/updmap.d/10texlive-base.cfg
/etc/texmf/updmap.d/10texlive-fonts-extra.cfg
/etc/texmf/updmap.d/10texlive-fonts-recommended.cfg
/etc/texmf/updmap.d/10texlive-latex-base.cfg
/etc/texmf/updmap.d/10texlive-latex-extra.cfg
/etc/texmf/updmap.d/10texlive-pictures.cfg
/usr/lib/mime/packages/texlive-base
/usr/share/texlive-base
/usr/share/texlive-bin
/usr/share/texmf-texlive
/usr/share/bug/texlive-base
/usr/share/bug/texlive-common
/usr/share/bug/texlive-doc-base
/usr/share/bug/texlive-doc-en
/usr/share/bug/texlive-fonts-extra


If you want to use tex or latex
- edit a file
$ vim centre.tex
- run latex on it 
$ latex centre
- look at the dvi file
$ xdvi centre
- generate ps file
$ dvips centre

---

