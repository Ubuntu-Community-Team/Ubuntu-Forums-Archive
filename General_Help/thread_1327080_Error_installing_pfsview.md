---
title: "Error installing pfsview"
date: 2009-11-15
forum: General Help
---

### Post by mbaddar on 2009-11-15
Hi all 
this is my first post here , i am not sure i am posting it under the right category or not :D

my platform is ubuntu 9.10 on VM , using vmplayer , on host os windows 
i tried to install pfsview library like that

sudo apt-get install pfsview 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
[B]The following packages have unmet dependencies:
  uim-qt: Depends: uim-qt3 (= 1:1.5.6-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/B]

i tried to do as it honts
apt-get install pfsview 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  uim-qt: Depends: uim-qt3 (= 1:1.5.6-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:~/Sources/pfstools-1.8.1_changed# apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gnuplot units libatlas3gf-base libcxsparse2.2.3 octave3.0 octave-pfstools libcamd2.2.0 groff
  octave-optim libglpk0 libgfortran3 libwxgtk2.8-0 libfftw3-3 ttf-liberation gnuplot-x11
  libwxbase2.8-0 gnuplot-nox libhdf5-serial-1.6.6-0 netpbm octave-signal libmagick++2
  libcholmod1.7.1 libpfs-1.2-0 libblas3gf libamd2.2.0 liblapack3gf psutils octave-specfun
  imagemagick octave-miscellaneous libumfpack5.4.0 octave3.0-common libqhull5 libreadline5
  libccolamd2.7.1 freeglut3 texinfo
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  uim-qt3
The following NEW packages will be installed:
  uim-qt3
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
1 not fully installed or removed.
Need to get 0B/258kB of archives.
After this operation, 782kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 131711 files and directories currently installed.)
Unpacking uim-qt3 (from .../uim-qt3_1%3a1.5.6-0ubuntu1_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/uim-qt3_1%3a1.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/locale/ja/LC_MESSAGES/uim.mo', which is also in package libuim-data 1:1.5.6-0ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/uim-qt3_1%3a1.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]i googled it a lot , some says that vm disk may be full but i checked it , others say use apt-get update then reinstall , but it didn't work

any help :D
thanks

---

