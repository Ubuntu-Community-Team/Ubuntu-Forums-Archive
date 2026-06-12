---
title: "Problem with apt"
date: 2011-04-25
forum: General Help
---

### Post by thalesfc on 2011-04-25
Dears,

I've tried to install kile on my new Ubuntu 10.10 using the usual command:

*apt-get install kile*

But got and error while installing texlive-base. 

So, i remove the previous instalation and tryed to install textlive-base.

Now, i'm receving this error message:

```
Setting up tex-common (2.08ubuntu0.1) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up texlive-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.wbrR2UxG
Please include this file if you report a bug.

dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-luatex (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for tex-common ...
texlive-base is not ready, delaying updmap-sys call
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.ELzHrpbE
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 texlive-base
 texlive-luatex
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Anyone knows how to solve it?

---

### Post by NoNameWill on 2011-04-25
```
sudo dpkg --configure -a
```

try this

---

### Post by thalesfc on 2011-04-25
Run an received this:

```
Setting up tex-common (2.08ubuntu0.1) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up texlive-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.IFWwrPRs
Please include this file if you report a bug.

dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-luatex (--configure):
 dependency problems - leaving unconfigured
Processing triggers for tex-common ...
texlive-base is not ready, delaying updmap-sys call
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.x779rbMV
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 texlive-base
 texlive-luatex
 tex-common

```

---

### Post by KegHead on 2011-04-25
Hi!

You can install kile via synaptic;

system..admin..synaptic..type in kile.

After installing, please update your system;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by thalesfc on 2011-04-25
I tried to install kile from synaptic and receive the following error message:

```
E: texlive-base: subprocess installed post-installation script returned error exit status 1
E: texlive-luatex: dependency problems - leaving unconfigured
E: texlive-latex-base: dependency problems - leaving unconfigured
E: texlive-generic-recommended: dependency problems - leaving unconfigured
E: texlive-pstricks: dependency problems - leaving unconfigured
E: asymptote: dependency problems - leaving unconfigured
E: texlive-metapost: dependency problems - leaving unconfigured
E: context: dependency problems - leaving unconfigured
E: texlive-fonts-recommended: dependency problems - leaving unconfigured
E: texlive-latex-recommended: dependency problems - leaving unconfigured
E: texlive: dependency problems - leaving unconfigured
E: texlive-bibtex-extra: dependency problems - leaving unconfigured
E: texlive-pictures: dependency problems - leaving unconfigured
E: texlive-latex-extra: dependency problems - leaving unconfigured
E: texlive-math-extra: dependency problems - leaving unconfigured
E: texlive-extra-utils: dependency problems - leaving unconfigured
E: dblatex: dependency problems - leaving unconfigured
E: texlive-font-utils: dependency problems - leaving unconfigured
E: feynmf: dependency problems - leaving unconfigured
E: kile: dependency problems - leaving unconfigured
E: latex-xcolor: dependency problems - leaving unconfigured
E: pgf: dependency problems - leaving unconfigured
E: latex-beamer: dependency problems - leaving unconfigured
E: latex2html: dependency problems - leaving unconfigured
E: prosper: dependency problems - leaving unconfigured
E: texlive-xetex: dependency problems - leaving unconfigured
E: tipa: dependency problems - leaving unconfigured
E: tex-common: subprocess installed post-installation script returned error exit status 1

```

---

### Post by thalesfc on 2011-04-25
When it was installing, it keep showing the message that locale can't find "pt_BR.UTF-8"

when i type:

*locale -a *

pt_br.utf8 is not installed. How can i install it?

---

### Post by KegHead on 2011-04-25
Hi!

I did the following;

sudo apt-get update

sudo apt-get install kile -f


jim@jim:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,097 B]                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,381 kB]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,023 kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.2 MB in 22s (600 kB/s)                                              
Reading package lists... Done
jim@jim:~$ sudo apt-get install kile -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xsl dvipng icoutils imagemagick kdebase-runtime kdebase-runtime-data
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools konsole
  kubuntu-debug-installer lacheck latex-beamer latex-xcolor libattica0 libcdt4
  libclucene0ldbl libgraph4 libgvc5 libilmbase6 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 liblqr-1-0 libmagickcore3 libmagickcore3-extra
  libmagickwand3 libmysqlclient16 libnepomuk4 libnepomukquery4a
  libnepomukutils4 libnetpbm10 libntrack-qt4-1 libntrack0 libopenexr6
  libpathplan4 libphonon4 libplasma3 libpolkit-qt-1-1 libqapt-runtime libqapt1
  libqca2 libqt4-declarative libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xmlpatterns libqtwebkit4 libreadline5
  libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libvirtodbc0 lmodern luatex mysql-common netpbm
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme pgf phonon
  phonon-backend-gstreamer plasma-scriptengine-declarative
  plasma-scriptengine-javascript prosper ps2eps psutils qapt-batch
  shared-desktop-ontologies soprano-daemon tex-common texlive texlive-base
  texlive-binaries texlive-common texlive-doc-base texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-pstricks texlive-pstricks-doc tipa virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libsaxon-java libxalan2-java docbook-xsl-saxon fop xalan
  dbtoepub libterm-readline-gnu-perl libterm-readline-perl-perl
  imagemagick-doc autotrace curl enscript ffmpeg gimp gnuplot grads hp2xx
  html2ps libwmf-bin mplayer povray radiance texlive-base-bin transfig
  ufraw-batch djvulibre-bin asymptote context dblatex latex2html tex4ht
  texlive-xetex lilypond kile-doc auctex hspell libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev
  phonon-backend-xine phonon-backend-vlc phonon-backend-mplayer debhelper
  texlive-doc-en perl-tk dvidvi fragmaster latexmk purifyeps xindy t1utils
The following NEW packages will be installed:
  docbook-xsl dvipng icoutils imagemagick kdebase-runtime kdebase-runtime-data
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools kile konsole
  kubuntu-debug-installer lacheck latex-beamer latex-xcolor libattica0 libcdt4
  libclucene0ldbl libgraph4 libgvc5 libilmbase6 libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 liblqr-1-0 libmagickcore3 libmagickcore3-extra
  libmagickwand3 libmysqlclient16 libnepomuk4 libnepomukquery4a
  libnepomukutils4 libnetpbm10 libntrack-qt4-1 libntrack0 libopenexr6
  libpathplan4 libphonon4 libplasma3 libpolkit-qt-1-1 libqapt-runtime libqapt1
  libqca2 libqt4-declarative libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xmlpatterns libqtwebkit4 libreadline5
  libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libvirtodbc0 lmodern luatex mysql-common netpbm
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme pgf phonon
  phonon-backend-gstreamer plasma-scriptengine-declarative
  plasma-scriptengine-javascript prosper ps2eps psutils qapt-batch
  shared-desktop-ontologies soprano-daemon tex-common texlive texlive-base
  texlive-binaries texlive-common texlive-doc-base texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-pstricks texlive-pstricks-doc tipa virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 upgraded, 121 newly installed, 0 to remove and 6 not upgraded.
Need to get 277 MB of archives.
After this operation, 599 MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by thalesfc on 2011-04-26
I tried:
[I]
sudo apt-get update
sudo apt-get install kile -f

[/I]and received the following error:

```
apt-get install kile -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kile is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
28 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up tex-common (2.08ubuntu0.1) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up texlive-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.jVejUGKw
Please include this file if you report a bug.

dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                  dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 asymptote depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-metapost (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of context:
 context depends on texlive-base (>= 2009); however:
  Package texlive-base is not configured yet.
 context depends on texlive-metapost (>= 2009); however:
  Package texlive-metapost is not configured yet.
dpkg: error processing context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2009-1); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2009-1); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-pictures (>= 2009-1); however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended (>= 2009-1); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of dblatex:
 dblatex depends on texlive (>= 2009); however:
  Package texlive is not configured yet.
 dblatex depends on texlive-bibtex-extra (>= 2009); however:
  Package texlive-bibtex-extra is not configured yet.
 dblatex depends on texlive-latex-extra (>= 2009); however:
  Package texlive-latex-extra is not configured yet.
 dblatex depends on texlive-math-extra (>= 2009); however:
  Package texlive-math-extra is not configured yet.
 dblatex depends on texlive-extra-utils (>= 2009); however:
  Package texlive-extra-utils is not configured yet.
dpkg: error processing dblatex (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of feynmf:
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
 feynmf depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.
dpkg: error processing feynmf (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kile:
 kile depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing kile (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of latex2html:
 latex2html depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 latex2html depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
 latex2html depends on texlive-latex-extra; however:
  Package texlive-latex-extra is not configured yet.
dpkg: error processing latex2html (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-luatex (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-xetex:
 texlive-xetex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-xetex depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-xetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
Processing triggers for tex-common ...
texlive-base is not ready, delaying updmap-sys call
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.iBuL2Ipn
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 texlive-base
 texlive-latex-base
 texlive-generic-recommended
 texlive-pstricks
 asymptote
 texlive-metapost
 context
 texlive-fonts-recommended
 texlive-latex-recommended
 texlive
 texlive-bibtex-extra
 texlive-pictures
 texlive-latex-extra
 texlive-math-extra
 texlive-extra-utils
 dblatex
 texlive-font-utils
 feynmf
 kile
 latex-xcolor
 pgf
 latex-beamer
 latex2html
 prosper
 texlive-luatex
 texlive-xetex
 tipa
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by KegHead on 2011-04-26
Hi!

It looks like you need to install texlive.


jim@jim:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,083 B]                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 2,627 B in 2s (985 B/s)
Reading package lists... Done
jim@jim:~$ sudo apt-get install texlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lacheck latex-beamer latex-xcolor lmodern luatex pgf prosper ps2eps
  tex-common texlive-base texlive-binaries texlive-common texlive-doc-base
  texlive-extra-utils texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base
  texlive-latex-base-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pstricks
  texlive-pstricks-doc tipa
Suggested packages:
  auctex debhelper texlive-doc-en perl-tk dvidvi fragmaster latexmk purifyeps
  xindy psutils t1utils
The following NEW packages will be installed:
  lacheck latex-beamer latex-xcolor lmodern luatex pgf prosper ps2eps
  tex-common texlive texlive-base texlive-binaries texlive-common
  texlive-doc-base texlive-extra-utils texlive-font-utils
  texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-pstricks texlive-pstricks-doc tipa
0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 217 MB of archives.
After this operation, 383 MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by thalesfc on 2011-04-26
[I]$ su
$ apt-get update[/I]
```
Hit http://br.archive.ubuntu.com maverick Release.gpg                                                                        
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                        
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                     
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                  
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                               
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                             
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                          
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                               
Ign http://br.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                            
Hit http://br.archive.ubuntu.com maverick-updates Release.gpg                                           
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                 
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                              
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                           
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                        
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                           
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                        
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                             
Ign http://br.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                          
Hit http://br.archive.ubuntu.com maverick Release                                                                             
Hit http://br.archive.ubuntu.com maverick-updates Release                                                                     
Hit http://br.archive.ubuntu.com maverick/main Sources                                                                        
Hit http://br.archive.ubuntu.com maverick/restricted Sources                                                                  
Hit http://br.archive.ubuntu.com maverick/universe Sources                                              
Hit http://br.archive.ubuntu.com maverick/multiverse Sources                                            
Hit http://br.archive.ubuntu.com maverick/main amd64 Packages                                           
Hit http://br.archive.ubuntu.com maverick/restricted amd64 Packages                                                           
Hit http://br.archive.ubuntu.com maverick/universe amd64 Packages                                                             
Hit http://br.archive.ubuntu.com maverick/multiverse amd64 Packages                                                           
Hit http://br.archive.ubuntu.com maverick-updates/main Sources                                          
Hit http://br.archive.ubuntu.com maverick-updates/restricted Sources                                                          
Hit http://br.archive.ubuntu.com maverick-updates/universe Sources                                                            
Hit http://br.archive.ubuntu.com maverick-updates/multiverse Sources                                    
Hit http://br.archive.ubuntu.com maverick-updates/main amd64 Packages                                   
Hit http://br.archive.ubuntu.com maverick-updates/restricted amd64 Packages                             
Hit http://br.archive.ubuntu.com maverick-updates/universe amd64 Packages                                                     
Hit http://br.archive.ubuntu.com maverick-updates/multiverse amd64 Packages                                                   
Hit http://extras.ubuntu.com maverick Release.gpg                                                                             
Hit http://security.ubuntu.com maverick-security Release.gpg                                            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release  
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Reading package lists... Done

```*$ apt-get upgrade*

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```**Instaling the  texlive**

*$ apt-get install texlive*

```
root@conselheiro:/home/thalesfc# apt-get install texlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  latex-beamer latex-xcolor pgf prosper texlive-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended texlive-generic-recommended texlive-latex-base
  texlive-latex-recommended texlive-pstricks tipa
Suggested packages:
  texlive-doc-en dvidvi fragmaster latexmk purifyeps xindy t1utils
The following NEW packages will be installed:
  latex-beamer latex-xcolor pgf prosper texlive texlive-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended texlive-generic-recommended texlive-latex-base
  texlive-latex-recommended texlive-pstricks tipa
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/69.7MB of archives.
After this operation, 148MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package texlive-base.
(Reading database ... 183345 files and directories currently installed.)
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
Selecting previously deselected package texlive-generic-recommended.
Unpacking texlive-generic-recommended (from .../texlive-generic-recommended_2009-10_all.deb) ...
Selecting previously deselected package texlive-pstricks.
Unpacking texlive-pstricks (from .../texlive-pstricks_2009-9ubuntu1_all.deb) ...
Selecting previously deselected package prosper.
Unpacking prosper (from .../prosper_1.00.4+cvs.2007.05.01-4_all.deb) ...
Selecting previously deselected package texlive-fonts-recommended.
Unpacking texlive-fonts-recommended (from .../texlive-fonts-recommended_2009-10_all.deb) ...
Selecting previously deselected package texlive.
Unpacking texlive (from .../texlive_2009-10_all.deb) ...
Selecting previously deselected package texlive-extra-utils.
Unpacking texlive-extra-utils (from .../texlive-extra-utils_2009-9ubuntu1_all.deb) ...
Selecting previously deselected package texlive-font-utils.
Unpacking texlive-font-utils (from .../texlive-font-utils_2009-9ubuntu1_all.deb) ...
Selecting previously deselected package tipa.
Unpacking tipa (from .../tipa_2%3a1.3-14_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 3 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for fontconfig ...
Setting up texlive-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.zGHqmdrm
Please include this file if you report a bug.

dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
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
 latex-bNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                                                                                                    eamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
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
 texlive-extra-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Processing triggers for tex-common ...
texlive-base is not ready, delaying updmap-sys call
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.zql5DgLD
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
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
 tipa
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by thalesfc on 2011-04-27
What can i do now?

---

