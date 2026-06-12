---
title: "deb installed software  depends  on none deb software"
date: 2011-08-20
forum: General Help
---

### Post by zhulianhua on 2011-08-20
Hello ! I installed  texlive2011 by DVD iso. Now I want to install Doxgen by apt-get but it depends 
on texlive . How to fix this? Or I have to install Doxgen without apt-get too ?
This is the code :
```
 fred@paradise:/opt/openfoam201/doc$sudo apt-get install doxygen
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  doxygen-latex lacheck latex-beamer latex-xcolor lmodern luatex pgf
  preview-latex-style prosper ps2eps tex-common texlive-base texlive-binaries
  texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-extra texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pictures
  texlive-pictures-doc texlive-pstricks texlive-pstricks-doc


```

---

### Post by akoskm on 2011-08-20
> **zhulianhua said:**
> Hello ! I installed  texlive2011 by DVD iso. Now I want to install Doxgen by apt-get but it depends 
on texlive . How to fix this? Or I have to install Doxgen without apt-get too ?
This is the code :
```
 fred@paradise:/opt/openfoam201/doc$sudo apt-get install doxygen
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  doxygen-latex lacheck latex-beamer latex-xcolor lmodern luatex pgf
  preview-latex-style prosper ps2eps tex-common texlive-base texlive-binaries
  texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-extra texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pictures
  texlive-pictures-doc texlive-pstricks texlive-pstricks-doc


```

I got confused, which one you installed as deb software and which one as none-deb software?
If you wan't to install doxygen from apt-then it obviously will depend on software from the repositories.
Why don't you install both software with apt?

---

### Post by madjr on 2011-08-20
install the one in the repos first and then upgrade?

also multiple versions might coexist

---

### Post by zhulianhua on 2011-08-20
I just want to install texlive in /opt not /usr ,so I use iso DVD .

---

### Post by akoskm on 2011-08-20
> **zhulianhua said:**
> I just want to install texlive in /opt not /usr ,so I use iso DVD .

Why are you doing such thing? Is installing programs to /opt instead of /usr is related to another problem?

---

