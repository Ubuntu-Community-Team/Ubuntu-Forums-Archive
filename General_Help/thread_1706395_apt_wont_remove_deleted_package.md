---
title: "apt wont remove deleted package"
date: 2011-03-13
forum: General Help
---

### Post by mzruya on 2011-03-13
hi, i'm trying to reinstall LaTeX after i manually deleted all of it's directories in /usr/share, apt-get can't seem to remove or install any of the packages,
```

sudo apt-get install -f
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libaiksaurus-1.2-data libwmf0.2-7 libicu42 libilmbase6 doc-base dvipng
  libboost-signals1.42.0 libuuid-perl libcdt4 librsvg2-bin ttf-lyx
  libpathplan4 libopenexr6 lyx-common netpbm libgvc5 libfreezethaw-perl
  libxdot4 psutils libnetpbm10 imagemagick libaiksaurus-1.2-0c2a
  libmagickcore3-extra libgraph4 libboost-regex1.42.0 texlive-pictures-doc
  texlive-science-doc libmldbm-perl libgd2-noxpm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.08) ...
Error: The new file /usr/share/tex-common/05TeXMF.cnf does not exist!
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
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
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-fonts-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2009-1); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2009-1); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-font-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-base
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-fonts-recommended
 texlive
 texlive-extra-utils
 texlive-font-utils
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 tipa
```

how can i fix apt's database ?
thanks !

---

### Post by lithopsian on 2011-03-13
You'll have to fix the tex-common configuration problem first, then everything else should fix itself.  I'm not familiar with that exact error, but maybe someone else has seen it before.

Or you could take a look at the postinst script for tex-common and see what it is trying to do.  You can even edit the script if necessary to make it not return an error in your situation, bit of course you risk it not working if you skip any critical processing.

---

