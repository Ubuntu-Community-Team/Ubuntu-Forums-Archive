---
title: "Update Manager - short read in buffer_copy"
date: 2010-09-26
forum: General Help
---

### Post by jafurcha on 2010-09-26
Upgraded from 9.04 to 9.10 and during the install, packages were not  installed due to errors. Went to synaptic package manager to fix 9  broken packages, but it could not fix them.

Previously had 10.04 working, even with the Intel Graphics Card  Incompatibility, but I downgraded to 7.10 due to a lot of major errors  and because it was the only disk I could find. Later I created  an  Ubuntu Live CD with 9.04 and installed it over 7.10 (not side by side)  which seemed to work, after which I tried to upgrade to 9.10 with  disastrous results, as installation of various packages failed.

Went to synaptic to fix 9 broken packages, found them with broken  packages filter, clicked fix broken packages in the edit enu and clicked  apply changes.

This is what happened when package manager tried to re-install broken packages:

-----------------------------------------------------------------------------------------------------

An error occurred

The following details are provided:
E: /var/cache/apt/archives/libicu40_4.0.1-2ubuntu2_i386.deb: short read  in buffer_copy (backend dpkg-deb during `./usr/lib/libicudata.so.40.1')
E:  /var/cache/apt/archives/firefox_3.6.10+build1+nobinonly-0ubuntu0.9.10.1_i386.deb:  short read in buffer_copy (backend dpkg-deb during  `./usr/lib/firefox-3.6.10/libxul.so')
E: /var/cache/apt/archives/gimp-help-common_2.4.1-2_all.deb: short read  in buffer_copy (backend dpkg-deb during  `./usr/share/gimp/2.0/help/images/tutorials/quickie-scale-dialog.png')
E: /var/cache/apt/archives/update-manager_1%3a0.126.10_all.deb: short  read in buffer_copy (backend dpkg-deb during  `./usr/share/gnome/help/update-manager/C/figures/synaptic-toggle-install-view.png')
E:  /var/cache/apt/archives/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb:  short read in buffer_copy (backend dpkg-deb during  `./usr/lib/libmysqlclient.so.15.0.0')

Results of Update Manager:

(Reading database ... 164819 files and directories currently installed.)
Unpacking libicu40 (from .../libicu40_4.0.1-2ubuntu2_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libicu40_4.0.1-2ubuntu2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libicudata.so.40.1')
No apport report written because the error message indicates a dpkg I/O error
                                                                              Preparing to replace firefox 3.6.10+build1+nobinonly-0ubuntu0.9.04.1  (using .../firefox_3.6.10+build1+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox_3.6.10+build1+nobinonly-0ubuntu0.9.10.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/firefox-3.6.10/libxul.so')
No apport report written because the error message indicates a dpkg I/O error
                                                                              Please restart all running instances of firefox, or you will experience  problems.
Preparing to replace gimp-help-common 2.4.1-1 (using .../gimp-help-common_2.4.1-2_all.deb) ...
Unpacking replacement gimp-help-common ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gimp-help-common_2.4.1-2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gimp/2.0/help/images/tutorials/quickie-scale-dialog.png')
No apport report written because the error message indicates a dpkg I/O error
                                                                              Preparing to replace update-manager 1:0.111.10 (using  .../update-manager_1%3a0.126.10_all.deb) ...
Unpacking replacement update-manager ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.126.10_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during  `./usr/share/gnome/help/update-manager/C/figures/synaptic-toggle-install-view.png')
No apport report written because MaxReports is reached already
                                                              Preparing  to replace libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.5 (using  .../libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
Unpacking replacement libmysqlclient15off ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libmysqlclient.so.15.0.0')
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libicu40_4.0.1-2ubuntu2_i386.deb
 /var/cache/apt/archives/firefox_3.6.10+build1+nobinonly-0ubuntu0.9.10.1_i386.deb
 /var/cache/apt/archives/gimp-help-common_2.4.1-2_all.deb
 /var/cache/apt/archives/update-manager_1%3a0.126.10_all.deb
 /var/cache/apt/archives/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of firefox-branding:
 firefox-branding depends on firefox (= 3.6.10+build1+nobinonly-0ubuntu0.9.10.1); however:
  Version of firefox on system is 3.6.10+build1+nobinonly-0ubuntu0.9.04.1.
dpkg: error processing firefox-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libicu40 (>= 4.0-1); however:
  Package libicu40 is not installed.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of couchdb-bin:
 couchdb-bin depends on libicu40 (>= 4.0-1); however:
  Package libicu40 is not installed.
dpkg: error processing couchdb-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty:
 brltty depends on libicu40 (>= 4.0-1); however:
  Package libicu40 is not installed.
dpkg: error processing brltty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.10+build1+nobinonly-0ubuntu0.9.10.1); however:
  Version of firefox on system is 3.6.10+build1+nobinonly-0ubuntu0.9.04.1.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwebkit-1.0-2:
 libwebkit-1.0-2 depends on libicu40 (>= 4.0-1); however:
  Package libicu40 is not installed.
dpkg: error processing libwebkit-1.0-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp-help-en:
 gimp-help-en depends on gimp-help-common (= 2.4.1-2); however:
  Version of gimp-help-common on system is 2.4.1-1.
dpkg: error processing gimp-help-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-branding; however:
  Package firefox-branding is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-base-core is not configured yet.
 openoffice.org-writer depends on libicu40 (>= 4.0-1); however:
  Package libicu40 is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
Setting up libdjvulibre21 (3.5.22-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Input/output error
dpkg: error processing libdjvulibre21 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmagickcore2:
 libmagickcore2 depends on libdjvulibre21 (>= 3.5.22); however:
  Package libdjvulibre21 is not configured yet.
dpkg: error processing libmagickcore2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on libwebkit-1.0-2 (>= 1.1.1); however:
  Package libwebkit-1.0-2 is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-emailmerge:
 openoffice.org-emailmerge depends on python-uno; however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb-bin (>= 0.10.0-0ubuntu3); however:
  Package couchdb-bin is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of obex-data-server:
 obex-data-server depends on libmagickcore2; however:
  Package libmagickcore2 is not configured yet.
dpkg: error processing obex-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmagickwand2:
 libmagickwand2 depends on libmagickcore2; however:
  Package libmagickcore2 is not configured yet.
dpkg: error processing libmagickwand2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-gnome-support; however:
  Package firefox-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.2); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty-x11:
 brltty-x11 depends on brltty (= 4.0-7ubuntu2); however:
  Package brltty is not configured yet.
dpkg: error processing brltty-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libdjvulibre21 (>= 3.5.22); however:
  Package libdjvulibre21 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libempathy-gtk28:
 libempathy-gtk28 depends on libwebkit-1.0-2 (>= 1.1.1); however:
  Package libwebkit-1.0-2 is not configured yet.
dpkg: error processing libempathy-gtk28 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-webkit:
 python-webkit depends on libwebkit-1.0-2 (>= 1.1.5); however:
  Package libwebkit-1.0-2 is not configured yet.
dpkg: error processing python-webkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rss-glx:
 rss-glx depends on libmagickcore2; however:
  Package libmagickcore2 is not configured yet.
 rss-glx depends on libmagickwand2; however:
  Package libmagickwand2 is not configured yet.
dpkg: error processing rss-glx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation-en-us:
 openoffice.org-hyphenation-en-us depends on openoffice.org (>= 1.0.3) | openoffice.org-writer; however:
  Package openoffice.org is not installed.
  Package openoffice.org-writer is not configured yet.
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on python-webkit; however:
  Package python-webkit is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-support-writing-en:
 language-support-writing-en depends on openoffice.org-hyphenation-en-us; however:
  Package openoffice.org-hyphenation-en-us is not configured yet.
dpkg: error processing language-support-writing-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-support-en:
 language-support-en depends on language-support-writing-en; however:
  Package language-support-writing-en is not configured yet.
dpkg: error processing language-support-en (--configure):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 firefox-branding
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 couchdb-bin
 brltty
 firefox-gnome-support
 libwebkit-1.0-2
 openoffice.org-calc
 gimp-help-en
 firefox-3.0-branding
 openoffice.org-base-core
 openoffice.org-writer
 libdjvulibre21
 python-uno
 libmagickcore2
 empathy
 openoffice.org-emailmerge
 openoffice.org-gnome
 desktopcouch
 openoffice.org-impress
 obex-data-server
 libmagickwand2
 firefox-3.0-gnome-support
 openoffice.org-math
 brltty-x11
 evince
 libempathy-gtk28
 python-webkit
 ubuntu-desktop
 rss-glx
 evolution-couchdb
 openoffice.org-hyphenation-en-us
 python-desktopcouch
 python-desktopcouch-records
 software-center
 language-support-writing-en
 language-support-en

---

