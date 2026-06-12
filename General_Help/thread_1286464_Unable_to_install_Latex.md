---
title: "Unable to install Latex"
date: 2009-10-09
forum: General Help
---

### Post by srinivas2828 on 2009-10-09
guys i was unable to install Latex getting strnage mesages when i use command like this
```

miriyala@VAIO:~$ sudo apt-get install latex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package latex is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package latex has no installation candidate

``````

miriyala@VAIO:~$ sudo apt-get install texlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tex-common texlive-base texlive-base-bin texlive-common texlive-doc-base
  texlive-fonts-recommended texlive-latex-base texlive-latex-recommended
Suggested packages:
  debhelper texlive-doc-en
Recommended packages:
  dvipdfmx lmodern perl-tk texlive-base-bin-doc texlive-fonts-recommended-doc
  tipa texlive-latex-base-doc latex-beamer latex-xcolor prosper
  texlive-latex-recommended-doc
The following NEW packages will be installed:
  tex-common texlive texlive-base texlive-base-bin texlive-common
  texlive-doc-base texlive-fonts-recommended texlive-latex-base
  texlive-latex-recommended
0 upgraded, 9 newly installed, 0 to remove and 14 not upgraded.
Need to get 3843kB/20.3MB of archives.
After this operation, 74.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tex-common texlive-base-bin texlive-doc-base
Install these packages without verification [y/N]? y
Err http://in.archive.ubuntu.com hardy/main tex-common 1.10
  404 Not Found
Err http://in.archive.ubuntu.com hardy/main texlive-base-bin 2007.dfsg.1-2
  404 Not Found
Err http://in.archive.ubuntu.com hardy/main texlive-doc-base 2007-3
  404 Not Found
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/tex-common/tex-common_1.10_all.deb  404 Not Found
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-base-bin_2007.dfsg.1-2_i386.deb  404 Not Found
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-doc/texlive-doc-base_2007-3_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```any idea what is going on

---

### Post by MelDJ on 2009-10-09
i dont know what latex is, but i think either the repository is down or unavailable from the 404 error which comes up.
try updating the latex repository (go to their site and get it perhaps) or change your software server

---

