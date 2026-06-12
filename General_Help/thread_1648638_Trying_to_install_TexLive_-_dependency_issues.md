---
title: "Trying to install TexLive - dependency issues"
date: 2010-12-19
forum: General Help
---

### Post by abraxyz on 2010-12-19
this is what i get:

```

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following NEW packages will be installed:
  lacheck{a} latex-beamer{a} latex-xcolor{a} lmodern{a} luatex{a} pgf{a} 
  prosper{a} ps2eps{a} tex-common{a} texlive texlive-base{a} 
  texlive-binaries{a} texlive-common{a} texlive-doc-base{a} 
  texlive-extra-utils{a} texlive-font-utils{a} texlive-fonts-recommended{a} 
  texlive-fonts-recommended-doc{a} texlive-generic-recommended{a} 
  texlive-latex-base{a} texlive-latex-base-doc{a} 
  texlive-latex-recommended{a} texlive-latex-recommended-doc{a} 
  texlive-luatex{a} texlive-pstricks{a} texlive-pstricks-doc{a} tipa{a} 
0 packages upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/217MB of archives. After unpacking 383MB will be used.
Do you want to continue? [Y/n/?] Writing extended state information...
Preconfiguring packages ...
Selecting previously deselected package lacheck. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 131825 files and directories currently installed.) 
Unpacking lacheck (from .../lacheck_1.26-11.1build1_i386.deb) ... 
Selecting previously deselected package tex-common. 
Unpacking tex-common (from .../tex-common_2.08_all.deb) ... 
Selecting previously deselected package texlive-common. 
Unpacking texlive-common (from .../texlive-common_2009-10_all.deb) ... 
Selecting previously deselected package texlive-binaries. 
Unpacking texlive-binaries (from .../texlive-binaries_2009-7_i386.deb) ... 
Selecting previously deselected package texlive-doc-base. 
Unpacking texlive-doc-base (from .../texlive-doc-base_2009-2_all.deb) ... 
Selecting previously deselected package luatex. 
Unpacking luatex (from .../luatex_0.60.1-1build2_i386.deb) ... 
Selecting previously deselected package texlive-base. 
Unpacking texlive-base (from .../texlive-base_2009-10_all.deb) ... 
Selecting previously deselected package texlive-latex-base. 
Unpacking texlive-latex-base (from .../texlive-latex-base_2009-10_all.deb) ... 
Selecting previously deselected package texlive-latex-recommended. 
Unpacking texlive-latex-recommended (from .../texlive-latex-recommended_2009-10_all.deb) ... 
Selecting previously deselected package latex-xcolor. 
Unpacking latex-xcolor (from .../latex-xcolor_2.11-1_all.deb) ... 
Selecting previously deselected package pgf. 
Unpacking pgf (from .../archives/pgf_2.00-1_all.deb) ... 
Selecting previously deselected package latex-beamer. 
Unpacking latex-beamer (from .../latex-beamer_3.07-2ubuntu1_all.deb) ... 
Selecting previously deselected package lmodern. 
Unpacking lmodern (from .../lmodern_2.004.1-3_all.deb) ... 
Selecting previously deselected package texlive-generic-recommended. 
Unpacking texlive-generic-recommended (from .../texlive-generic-recommended_2009-10_all.deb) ... 
Selecting previously deselected package texlive-pstricks. 
Unpacking texlive-pstricks (from .../texlive-pstricks_2009-9ubuntu1_all.deb) ... 
Selecting previously deselected package prosper. 
Unpacking prosper (from .../prosper_1.00.4+cvs.2007.05.01-4_all.deb) ... 
Selecting previously deselected package ps2eps. 
Unpacking ps2eps (from .../ps2eps_1.64-6build1_i386.deb) ... 
Selecting previously deselected package texlive-fonts-recommended. 
Unpacking texlive-fonts-recommended (from .../texlive-fonts-recommended_2009-10_all.deb) ... 
Selecting previously deselected package texlive. 
Unpacking texlive (from .../texlive_2009-10_all.deb) ... 
Selecting previously deselected package texlive-extra-utils. 
Unpacking texlive-extra-utils (from .../texlive-extra-utils_2009-9ubuntu1_all.deb) ... 
Selecting previously deselected package texlive-font-utils. 
Unpacking texlive-font-utils (from .../texlive-font-utils_2009-9ubuntu1_all.deb) ... 
Selecting previously deselected package texlive-fonts-recommended-doc. 
Unpacking texlive-fonts-recommended-doc (from .../texlive-fonts-recommended-doc_2009-10_all.deb) ... 
Selecting previously deselected package texlive-latex-base-doc. 
Unpacking texlive-latex-base-doc (from .../texlive-latex-base-doc_2009-10_all.deb) ... 
Selecting previously deselected package texlive-latex-recommended-doc. 
Unpacking texlive-latex-recommended-doc (from .../texlive-latex-recommended-doc_2009-10_all.deb) ... 
Selecting previously deselected package texlive-luatex. 
Unpacking texlive-luatex (from .../texlive-luatex_2009-10_all.deb) ... 
Selecting previously deselected package texlive-pstricks-doc. 
Unpacking texlive-pstricks-doc (from .../texlive-pstricks-doc_2009-9ubuntu1_all.deb) ... 
Selecting previously deselected package tipa. 
Unpacking tipa (from .../tipa_2%3a1.3-14_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for doc-base ... 
Processing 7 added doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for install-info ... 
Processing triggers for fontconfig ... 
Setting up lacheck (1.26-11.1build1) ... 
Setting up tex-common (2.08) ... 
Running mktexlsr. This may take some time... done. 
texlive-base is not ready, delaying updmap-sys call 
texlive-base is not ready, skipping fmtutil-sys --all call 
Setting up texlive-common (2009-10) ... 
Setting up texlive-binaries (2009-7) ... 
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode. 
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode. 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...  
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE...  
mktexlsr: Updating /var/lib/texmf/ls-R...  
mktexlsr: Done. 
Building format(s) --refresh. 
    This may take some time... done. 
Setting up texlive-doc-base (2009-2) ... 
Setting up luatex (0.60.1-1build2) ... 
texlive-base is not ready, cannot create formats 
Setting up lmodern (2.004.1-3) ... 
Running mktexlsr. This may take some time... done. 
Updating fontconfig cache for /usr/share/texmf/fonts/type1/public/lm 
Updating fontconfig cache for /usr/share/texmf/fonts/type1/public/lm 
Setting up ps2eps (1.64-6build1) ... 
Setting up texlive-fonts-recommended-doc (2009-10) ... 
Setting up texlive-latex-base-doc (2009-10) ... 
Setting up texlive-latex-recommended-doc (2009-10) ... 
Setting up texlive-pstricks-doc (2009-9ubuntu1) ... 
Processing triggers for tex-common ... 
Running mktexlsr. This may take some time... done. 
texlive-base is not ready, delaying updmap-sys call 
Setting up texlive-base (2009-10) ... 
Running mktexlsr. This may take some time... done. 
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf. 
    This may take some time... done. 
Processing triggers for tex-common ... 
Running updmap-sys. This may take some time... done. 
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def. 
    This may take some time... done. 
Setting up texlive-generic-recommended (2009-10) ... 
Setting up texlive-fonts-recommended (2009-10) ... 
Setting up texlive-extra-utils (2009-9ubuntu1) ... 
Setting up texlive-font-utils (2009-9ubuntu1) ... 
Setting up texlive-luatex (2009-10) ... 
Setting up texlive-latex-base (2009-10) ... 
Running mktexlsr. This may take some time... done. 
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf. 
    This may take some time...  
fmtutil-sys failed. Output has been stored in 
/tmp/fmtutil.PJseNS1k 
Please include this file if you report a bug. 
 
dpkg: error processing texlive-latex-base (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of texlive-latex-recommended: 
 texlive-latex-recommended depends on texlive-latex-base (>= 2009-1); however: 
  Package texlive-latex-base is not configured yet. 
dpkg: error processing texlive-latex-recommended (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of latex-xcolor: 
 latex-xcolor depends on texlive-latex-recommended; however: 
  Package texlive-latex-recommended is not configured yet. 
dpkg: error processing latex-xcolor (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of pgf: 
 pgf depends on latex-xcolor (>= 2.00-1); however: 
  Package latex-xcolor is not configured yet. 
 pgf depends on texlive-latex-recommended; however: 
  Package texlive-latex-recommended is not configured yet. 
dpkg: error processing pgf (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of latex-beamer: 
 latex-beamer depends on pgf (>= 1.00-1); however: 
  Package pgf is not configured yet. 
 latex-beamer depends on latex-xcolor (>= 2.00-1); however: 
  Package latex-xcolor is not configured yet. 
 latex-beamer depends on texlive-latex-base; however: 
  Package texlive-latex-base is not configured yet. 
dpkg: error processing latex-beamer (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of prosper: 
 prosper depends on texlive-latex-base; however: 
  Package texlive-latex-base is not configured yet. 
 prosper depends on texlive-latex-recommended; however: 
  Package texlive-latex-recommended is not configured yet. 
dpkg: error processing prosper (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of texlive: 
 texlive depends on texlive-latex-recommended (>= 2009-1); however: 
  Package texlive-latex-recommended is not configured yet. 
 texlive depends on texlive-latex-base (>= 2009-1); however: 
  Package texlive-latex-base is not configured yet. 
dpkg: error processing texlive (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tipa: 
 tipa depends on texlive-latex-base; however: 
  Package texlive-latex-base is not configured yet. 
dpkg: error processing tipa (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for tex-common ... 
Running mktexlsr. This may take some time... done. 
Running updmap-sys. This may take some time... done. 
Setting up texlive-pstricks (2009-9ubuntu1) ... 
Processing triggers for tex-common ... 
Running mktexlsr. This may take some time... done. 
Errors were encountered while processing: 
 texlive-latex-base 
 texlive-latex-recommended 
 latex-xcolor 
 pgf 
 latex-beamer 
 prosper 
 texlive 
 tipa 
Setting up texlive-latex-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
    This may take some time... Processing triggers for tex-common ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...

```please, help...
thanks

---

### Post by karthick87 on 2010-12-19
Try,
```
sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by abraxyz on 2010-12-19
that didn't work : (

---

### Post by karthick87 on 2010-12-19
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```

---

### Post by abraxyz on 2010-12-20
> **karthick87 said:**
> ```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```

i get the same errors

---

### Post by angryjohnny99 on 2010-12-20
Hello everybody,

i had the same problem trying to install texlive. 
today i was able to fix this issue on my system:

there is a line appearing during the installation process like f.e.:

```
fmtutil-sys failed. Output has been stored in 
/tmp/fmtutil.PJseNS1k 
Please include this file if you report a bug. 
``` 

Calling the above file /tmp/fmutil... , i found out what the real problem was:
a few weeks ago i manually installed zlib-1.2.5 on my system.
there seems to be a compatibility issue between  zlib-1.2.5 and the luatex version integrated in the texlive
distribution.  thus i manually uninstalled zlib-1.2.5 calling make uninstall in the relevant folder  and installed the version 1.2.3.4 using synaptic (the package is called zlib1g).
After that i completely removed all packages related to texlive with synaptic and reinstalled them.
Then everything was working.

---

### Post by abraxyz on 2010-12-21
unfortunately, not the case with me..

---

### Post by angryjohnny99 on 2010-12-22
looking at the fmtutil it seems to have s.th. to do with the  file ushyphen.tex because of the following line:

```
(/usr/local/share/texmf/tex/latex/tex/generic/babel/hyphen.cfg
! I can't find file `ushyphen.tex
```'.

i found another post within this [link]("http://ubuntuforums.org/archive/index.php/t-1329626.html") which contains the following hint:

```
Thanks Chronon, I fixed it...

Looking in /tmp/fmtutil.xxxxxxxx I found out that the file "ushyph.tex"  was missing and this caused all the trouble.  Tried to "find" it, and  the file was really nowhere to be found on my machine.  Got it from  http://www.ctan.org/tex-archive/language/hyphenation/ushyph/ and stuck  it into my /usr/share/texmf-texlive/tex/generic/hyphen/.  After that, a
sudo apt-get install -f
fixed the broken package and everything is working fine now.

Since ushyph.tex was needed and wasn't in the package I downloaded, I  reported this as a bug too.  But the above should be a work-around for  those few that run into the same problem as I did.

The machine is a pretty prestine Dell laptop - just wiped Windows off of  it and freshly installed Karmic Koala from scratch.  Why you got off  the hook without the file is still a mystery to me...  Are you in the US  (as this is apparently a country-specific hyphenation file)?

```Perhaps that will help.

---

