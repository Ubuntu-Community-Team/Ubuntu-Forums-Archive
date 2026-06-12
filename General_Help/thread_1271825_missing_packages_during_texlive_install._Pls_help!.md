---
title: "missing packages during texlive install. Pls help!"
date: 2009-09-21
forum: General Help
---

### Post by ubunyou on 2009-09-21
Hello,
I am trying to install texlive via the 'agt-get install texlive-full' and am getting a lot of 404 not found errors during the install.

I ran 'apt-get clean all' and 'apt-get upgrade' successfully before the install to ensure apt-get was properly synced with the repositories.

Is texlive still maintained on Gutsy? Am I doing something wrong?

Any help is much appreciated, even if it a simple confirmation that I need to upgrade to 8.04.

Thanks!!!



Some system info: 
root@kz-laptop:~# uname -a
Linux blah 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux


root@kz-laptop:~# apt-config  dump
(note output has been de-smilied for posting :))
APT "";
APT :: Architecture "i386";
APT :: Build-Essential "";
APT :: Build-Essential ::  "build-essential";
APT :: Install-Recommends "0";
APT :: Install-Suggests "0";
APT :: Authentication "";
APT :: Authentication :: TrustCDROM "true";
APT :: NeverAutoRemove "";
APT :: NeverAutoRemove ::  "^linux-image.*";
APT :: NeverAutoRemove ::  "^linux-restricted-modules.*";
APT :: NeverAutoRemove ::  "^linux-ubuntu-modules-.*";
APT :: Never-MarkAuto-Sections "";
APT :: Never-MarkAuto-Sections ::  "metapackages";
APT :: Never-MarkAuto-Sections ::  "restricted/metapackages";
APT :: Never-MarkAuto-Sections ::  "universe/metapackages";
APT :: Never-MarkAuto-Sections ::  "multiverse/metapackages";
APT :: Install-Recommends-Sections "";
APT :: Install-Recommends-Sections ::  "metapackages";
APT :: Install-Recommends-Sections ::  "restricted/metapackages";
APT :: Install-Recommends-Sections ::  "universe/metapackages";
APT :: Install-Recommends-Sections ::  "multiverse/metapackages";
APT :: Periodic "";
APT :: Periodic :: Update-Package-Lists "1";
APT :: Periodic :: Download-Upgradeable-Packages "0";
APT :: Periodic :: AutocleanInterval "0";
APT :: Archives "";
APT :: Archives :: MaxAge "30";
APT :: Archives :: MinAge "2";
APT :: Archives :: MaxSize "500";
APT :: Acquire "";
APT :: Acquire :: Translation "environment";
Dir "/";
Dir :: State "var/lib/apt/";
Dir :: State :: lists "lists/";
Dir :: State :: cdroms "cdroms.list";
Dir :: State :: mirrors "mirrors/";
Dir :: State :: userstatus "status.user";
Dir :: State :: status "/var/lib/dpkg/status";
Dir :: Cache "var/cache/apt/";
Dir :: Cache :: archives "archives/";
Dir :: Cache :: srcpkgcache "srcpkgcache.bin";
Dir :: Cache :: pkgcache "pkgcache.bin";
Dir :: Etc "etc/apt/";
Dir :: Etc :: sourcelist "sources.list";
Dir :: Etc :: sourceparts "sources.list.d";
Dir :: Etc :: vendorlist "vendors.list";
Dir :: Etc :: vendorparts "vendors.list.d";
Dir :: Etc :: main "apt.conf";
Dir :: Etc :: parts "apt.conf.d";
Dir :: Etc :: preferences "preferences";
Dir :: Bin "";
Dir :: Bin :: methods "/usr/lib/apt/methods";
Dir :: Bin :: dpkg "/usr/bin/dpkg";
Dir :: Log "var/log/apt";
Dir :: Log :: Terminal "term.log";
aptitude "";
aptitude :: Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude :: Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade :: Allowed-Origins "";
Unattended-Upgrade :: Allowed-Origins ::  "Ubuntu gutsy-security";
DPkg "";
DPkg :: Pre-Install-Pkgs "";
DPkg :: Pre-Install-Pkgs ::  "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg :: Post-Invoke "";
DPkg :: Post-Invoke ::  "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi"


and the output of my failed attempt:
root@kz-laptop:~# apt-get clean all

root@kz-laptop:~# apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

root@kz-laptop:~# apt-get install texlive-full
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cm-super context feynmf latex-beamer latex-xcolor lcdf-typetools libkpathsea-dev lmodern musixlyr musixtex musixtex-slurps pfb2t1c2pfb pgf
  preview-latex-style t1utils tetex-bin tetex-extra tex-common tex4ht tex4ht-common texinfo texlive texlive-base texlive-base-bin texlive-bibtex-extra
  texlive-common texlive-doc-base texlive-doc-bg texlive-doc-cs+sk texlive-doc-de texlive-doc-el texlive-doc-en texlive-doc-es texlive-doc-fi
  texlive-doc-fr texlive-doc-it texlive-doc-ja texlive-doc-ko texlive-doc-mn texlive-doc-nl texlive-doc-pl texlive-doc-pt texlive-doc-ru texlive-doc-th
  texlive-doc-tr texlive-doc-uk texlive-doc-vi texlive-doc-zh texlive-extra-utils texlive-font-utils texlive-fonts-extra texlive-fonts-recommended
  texlive-formats-extra texlive-games texlive-generic-extra texlive-generic-recommended texlive-humanities texlive-lang-african texlive-lang-arab
  texlive-lang-armenian texlive-lang-croatian texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-danish texlive-lang-dutch texlive-lang-finnish
  texlive-lang-french texlive-lang-german texlive-lang-greek texlive-lang-hebrew texlive-lang-hungarian texlive-lang-indic texlive-lang-italian
  texlive-lang-latin texlive-lang-manju texlive-lang-mongolian texlive-lang-norwegian texlive-lang-other texlive-lang-polish texlive-lang-portuguese
  texlive-lang-spanish texlive-lang-swedish texlive-lang-tibetan texlive-lang-ukenglish texlive-lang-vietnamese texlive-latex-base texlive-latex-extra
  texlive-latex-recommended texlive-latex3 texlive-math-extra texlive-metapost texlive-music texlive-omega texlive-pictures texlive-plain-extra
  texlive-pstricks texlive-publishers texlive-science texlive-xetex
Suggested packages:
  perl-tk fontforge context-nonfree context-doc-nonfree pmx m-tx debhelper imagemagick netpbm passivetex jadetex xmltex
Recommended packages:
  dvipng dvipdfmx dviutils dvi2tty lacheck texpower tipa latex-cjk-all latex-sanskrit prosper
The following NEW packages will be installed:
  cm-super context feynmf latex-beamer latex-xcolor lcdf-typetools libkpathsea-dev lmodern musixlyr musixtex musixtex-slurps pfb2t1c2pfb pgf
  preview-latex-style t1utils tetex-bin tetex-extra tex-common tex4ht tex4ht-common texinfo texlive texlive-base texlive-base-bin texlive-bibtex-extra
  texlive-common texlive-doc-base texlive-doc-bg texlive-doc-cs+sk texlive-doc-de texlive-doc-el texlive-doc-en texlive-doc-es texlive-doc-fi
  texlive-doc-fr texlive-doc-it texlive-doc-ja texlive-doc-ko texlive-doc-mn texlive-doc-nl texlive-doc-pl texlive-doc-pt texlive-doc-ru texlive-doc-th
  texlive-doc-tr texlive-doc-uk texlive-doc-vi texlive-doc-zh texlive-extra-utils texlive-font-utils texlive-fonts-extra texlive-fonts-recommended
  texlive-formats-extra texlive-full texlive-games texlive-generic-extra texlive-generic-recommended texlive-humanities texlive-lang-african
  texlive-lang-arab texlive-lang-armenian texlive-lang-croatian texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-danish texlive-lang-dutch
  texlive-lang-finnish texlive-lang-french texlive-lang-german texlive-lang-greek texlive-lang-hebrew texlive-lang-hungarian texlive-lang-indic
  texlive-lang-italian texlive-lang-latin texlive-lang-manju texlive-lang-mongolian texlive-lang-norwegian texlive-lang-other texlive-lang-polish
  texlive-lang-portuguese texlive-lang-spanish texlive-lang-swedish texlive-lang-tibetan texlive-lang-ukenglish texlive-lang-vietnamese
  texlive-latex-base texlive-latex-extra texlive-latex-recommended texlive-latex3 texlive-math-extra texlive-metapost texlive-music texlive-omega
  texlive-pictures texlive-plain-extra texlive-pstricks texlive-publishers texlive-science texlive-xetex
0 upgraded, 100 newly installed, 0 to remove and 0 not upgraded.
Need to get 500MB of archives.
After unpacking, 1035MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  tex-common texlive-common texlive-doc-base texlive-base-bin texlive-base texlive-latex-base texlive-latex-recommended texlive-lang-danish
  texlive-lang-vietnamese texlive-lang-polish texlive-lang-mongolian texlive-lang-french texlive-lang-swedish texlive-pictures texlive-lang-greek
  texlive-lang-croatian texlive-fonts-extra texlive-fonts-recommended texlive tetex-bin texlive-lang-spanish preview-latex-style texlive-latex-extra
  texlive-lang-norwegian texlive-lang-german texlive-lang-cyrillic texlive-font-utils texlive-lang-finnish texlive-generic-recommended texlive-pstricks
  texlive-lang-portuguese texlive-lang-other texlive-bibtex-extra texlive-lang-czechslovak texlive-math-extra texlive-lang-italian texlive-publishers
  texlive-lang-dutch texlive-lang-hungarian texlive-lang-latin tetex-extra pfb2t1c2pfb cm-super texlive-metapost lmodern context texlive-extra-utils
  feynmf latex-xcolor pgf latex-beamer lcdf-typetools libkpathsea-dev musixlyr musixtex musixtex-slurps t1utils tex4ht-common tex4ht texinfo
  texlive-doc-bg texlive-doc-cs+sk texlive-doc-de texlive-doc-el texlive-doc-en texlive-doc-es texlive-doc-fi texlive-doc-fr texlive-doc-it
  texlive-doc-ja texlive-doc-ko texlive-doc-mn texlive-doc-nl texlive-doc-pl texlive-doc-pt texlive-doc-ru texlive-doc-th texlive-doc-tr texlive-doc-uk
  texlive-doc-vi texlive-doc-zh texlive-formats-extra texlive-science texlive-xetex texlive-omega texlive-lang-indic texlive-plain-extra
  texlive-generic-extra texlive-lang-hebrew texlive-lang-arab texlive-lang-ukenglish texlive-lang-manju texlive-music texlive-games texlive-lang-tibetan
  texlive-lang-armenian texlive-latex3 texlive-lang-african texlive-humanities texlive-full
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tex-common 1.9
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-common 2007-10
  404 Not Found
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-base 2007-3 [750kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-base 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-latex-base 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-latex-recommended 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-danish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-vietnamese 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-polish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-mongolian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-french 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-swedish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-pictures 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-greek 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-croatian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-fonts-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-fonts-recommended 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tetex-bin 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-spanish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main preview-latex-style 11.83-7ubuntu1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-latex-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-norwegian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-german 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-cyrillic 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-finnish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-generic-recommended 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-pstricks 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-portuguese 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-other 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-bibtex-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-czechslovak 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-math-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-italian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-publishers 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-dutch 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-hungarian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-latin 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tetex-extra 2007-10
  404 Not Found
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe pfb2t1c2pfb 0.3-3 [9900B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe cm-super 0.3.3-5
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe lmodern 1.010x-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe context 2007.04.17-1
  404 Not Found
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe feynmf 1.08-4 [402kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main latex-xcolor 2.09-1
  404 Not Found
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main pgf 1.18-1 [2976kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main latex-beamer 3.07-1 [2192kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe lcdf-typetools 2.62-2
  404 Not Found
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe musixlyr 2.1c-3 [55.0kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe musixtex 1:0.112.2-3 [4947kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe musixtex-slurps 92a-5
  404 Not Found
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe t1utils 1.32-1 [53.8kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tex4ht-common 20070717-2
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tex4ht 20070717-2
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texinfo 4.8.dfsg.1-6
  404 Not Found
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-bg 2007-3 [2077kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-cs+sk 2007-3 [1503kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-de 2007-3 [4076kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-el 2007-3 [424kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-en 2007-3 [30.8MB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-es 2007-3 [1180kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-fi 2007-3 [1761kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-fr 2007-3 [6593kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-it 2007-3 [1578kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-ja 2007-3 [666kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-ko 2007-3 [1139kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-mn 2007-3 [40.9kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-nl 2007-3 [1993kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-pl 2007-3 [5149kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-pt 2007-3 [4788kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-ru 2007-3 [2388kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-th 2007-3 [492kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-tr 2007-3 [1474kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-uk 2007-3 [2143kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-vi 2007-3 [3316kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-doc-zh 2007-3 [563kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-formats-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-science 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-plain-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-generic-extra 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-hebrew 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-arab 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-ukenglish 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-manju 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-games 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-tibetan 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-armenian 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-latex3 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main texlive-lang-african 2007.dfsg.1-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-humanities 2007-3
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe texlive-full 2007-10
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main texlive-base-bin 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main texlive-font-utils 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe texlive-metapost 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main texlive-extra-utils 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main libkpathsea-dev 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe texlive-xetex 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe texlive-omega 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main texlive-lang-indic 2007-12ubuntu3.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe texlive-music 2007-12ubuntu3.1
  404 Not Found
Fetched 85.5MB in 6m15s (228kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tex-common/tex-common_1.9_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tex-common/tex-common_1.9_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-common_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-common_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-base-bin_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-base-bin_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-base_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-base_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-danish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-danish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-vietnamese_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-vietnamese_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-polish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-polish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-mongolian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-mongolian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-french_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-french_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-swedish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-swedish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-pictures_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-pictures_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-greek_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-greek_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-croatian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-croatian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-fonts-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-fonts-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/tetex-bin_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/tetex-bin_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-spanish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-spanish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/auctex/preview-latex-style_11.83-7ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/auctex/preview-latex-style_11.83-7ubuntu1_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-norwegian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-norwegian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-german_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-german_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-cyrillic_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-cyrillic_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-font-utils_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-font-utils_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-finnish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-finnish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-generic-recommended_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-generic-recommended_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-pstricks_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-pstricks_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-portuguese_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-portuguese_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-other_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-other_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-bibtex-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-bibtex-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-czechslovak_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-czechslovak_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-math-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-math-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-italian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-italian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-publishers_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-publishers_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-dutch_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-dutch_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-hungarian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-hungarian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-latin_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-latin_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/tetex-extra_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/tetex-extra_2007-10_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/cm-super/cm-super_0.3.3-5_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/cm-super/cm-super_0.3.3-5_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-metapost_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-metapost_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/lmodern/lmodern_1.010x-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/lmodern/lmodern_1.010x-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/c/context/context_2007.04.17-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/context/context_2007.04.17-1_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-extra-utils_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-extra-utils_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/latex-xcolor/latex-xcolor_2.09-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/latex-xcolor/latex-xcolor_2.09-1_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/l/lcdf-typetools/lcdf-typetools_2.62-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/l/lcdf-typetools/lcdf-typetools_2.62-2_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea-dev_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea-dev_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/m/musixtex-slurps/musixtex-slurps_92a-5_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/musixtex-slurps/musixtex-slurps_92a-5_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tex4ht/tex4ht-common_20070717-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tex4ht/tex4ht-common_20070717-2_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tex4ht/tex4ht_20070717-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tex4ht/tex4ht_20070717-2_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.8.dfsg.1-6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texinfo/texinfo_4.8.dfsg.1-6_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-formats-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-formats-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-science_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-science_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-xetex_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-xetex_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-omega_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-omega_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-lang-indic_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-lang-indic_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-plain-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-plain-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-generic-extra_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-generic-extra_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-hebrew_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-hebrew_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-arab_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-arab_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-ukenglish_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-ukenglish_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-manju_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-manju_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-music_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-bin/texlive-music_2007-12ubuntu3.1_i386.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-games_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-games_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-tibetan_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-tibetan_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-armenian_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-armenian_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-latex3_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-latex3_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-african_2007.dfsg.1-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-lang/texlive-lang-african_2007.dfsg.1-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-humanities_2007-3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-extra/texlive-humanities_2007-3_all.deb) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-base/texlive-full_2007-10_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/texlive-base/texlive-full_2007-10_all.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by ubunyou on 2009-09-24
bump?

---

### Post by ubunyou on 2009-09-27
works fine in Hardy

---

### Post by Stefan_K on 2009-09-28
I'm already using the [upcoming TeX Live 2009]("http://texblog.net/latex-archive/news/tex-live-2009-pretest/") and TL 2008 before. To fulfill dependencies I've used equivs, if you want to know more, look at [Kile and TeX Live 2008 on Ubuntu Linux]("http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/").

Stefan


--
[TeXblog]("http://texblog.net")

---

