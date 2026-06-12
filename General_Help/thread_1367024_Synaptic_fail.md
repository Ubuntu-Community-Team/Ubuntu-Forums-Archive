---
title: "Synaptic fail"
date: 2009-12-29
forum: General Help
---

### Post by TheNessus on 2009-12-29
E: kcm-gtk-kde4: subprocess installed post-removal script returned error exit status 2

hmmm... ideas?

cant install or remove anything.

---

### Post by MelDJ on 2009-12-29
tried *sudo dpkg --configure -a ?*

---

### Post by TheNessus on 2009-12-29
no effect

---

### Post by TheNessus on 2009-12-29
bump

---

### Post by TheNessus on 2009-12-29
forrest bump

---

### Post by TheNessus on 2009-12-29
argh!


jeff@jeff-laptop:~$ sudo apt-get remove kcm-gtk-kde4
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  empathy-doc libxml-rss-perl libmd5-perl libgtk2-sexy-perl
  libcrypt-ssleay-perl libdatetime-locale-perl libparams-validate-perl
  libxml-namespacesupport-perl libpst4 google-gadgets-common libqt4-core
  libgtk2-trayicon-perl google-gadgets-gst libempathy-gtk28
  libxml-sax-expat-perl libanculus0.3-cil libsoup2.2-8 libcrypt-simple-perl
  pidgin-data libmono-winforms2.0-cil libqt4-gui google-gadgets-xul
  libmono-webbrowser0.5-cil libgluezilla libcrypt-blowfish-perl
  libxml-sax-perl libdatetime-perl libggadget-gtk-1.0-0 libgtk2-gladexml-perl
  libwebkit1.0-cil libdatetime-format-w3cdtf-perl libxml-simple-perl
  nexuiz-data libmono-accessibility2.0-cil libggadget-1.0-0
  libdatetime-format-mail-perl libsexymm2 libdatetime-timezone-perl
  libemail-mime-encodings-perl liblist-moreutils-perl libclass-singleton-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kcm-gtk-kde4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,949kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 271710 files and directories currently installed.)
Removing kcm-gtk-kde4 ...
cd: 2: can't cd to /usr/share/kubuntu-default-settings/
dpkg: error processing kcm-gtk-kde4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kcm-gtk-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-laptop:~$ sudo apt-get upgrade kcm-gtk-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kcm-gtk-kde4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,949kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 271710 files and directories currently installed.)
Removing kcm-gtk-kde4 ...
cd: 2: can't cd to /usr/share/kubuntu-default-settings/
dpkg: error processing kcm-gtk-kde4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kcm-gtk-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-laptop:~$ sudo apt-get update kcm-gtk-kde4
E: The update command takes no arguments
jeff@jeff-laptop:~$ sudo apt-get install kcm-gtk-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kcm-gtk-kde4 is already the newest version.
The following packages were automatically installed and are no longer required:
  empathy-doc libxml-rss-perl libmd5-perl libgtk2-sexy-perl
  libcrypt-ssleay-perl libdatetime-locale-perl libparams-validate-perl
  libxml-namespacesupport-perl libpst4 google-gadgets-common libqt4-core
  libgtk2-trayicon-perl google-gadgets-gst libempathy-gtk28
  libxml-sax-expat-perl libanculus0.3-cil libsoup2.2-8 libcrypt-simple-perl
  pidgin-data libmono-winforms2.0-cil libqt4-gui google-gadgets-xul
  libmono-webbrowser0.5-cil libgluezilla libcrypt-blowfish-perl
  libxml-sax-perl libdatetime-perl libggadget-gtk-1.0-0 libgtk2-gladexml-perl
  libwebkit1.0-cil libdatetime-format-w3cdtf-perl libxml-simple-perl
  nexuiz-data libmono-accessibility2.0-cil libggadget-1.0-0
  libdatetime-format-mail-perl libsexymm2 libdatetime-timezone-perl
  libemail-mime-encodings-perl liblist-moreutils-perl libclass-singleton-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kcm-gtk-kde4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,949kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 271710 files and directories currently installed.)
Removing kcm-gtk-kde4 ...
cd: 2: can't cd to /usr/share/kubuntu-default-settings/
dpkg: error processing kcm-gtk-kde4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kcm-gtk-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-laptop:~$ sudo apt-get purge kcm-gtk-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  empathy-doc libxml-rss-perl libmd5-perl libgtk2-sexy-perl
  libcrypt-ssleay-perl libdatetime-locale-perl libparams-validate-perl
  libxml-namespacesupport-perl libpst4 google-gadgets-common libqt4-core
  libgtk2-trayicon-perl google-gadgets-gst libempathy-gtk28
  libxml-sax-expat-perl libanculus0.3-cil libsoup2.2-8 libcrypt-simple-perl
  pidgin-data libmono-winforms2.0-cil libqt4-gui google-gadgets-xul
  libmono-webbrowser0.5-cil libgluezilla libcrypt-blowfish-perl
  libxml-sax-perl libdatetime-perl libggadget-gtk-1.0-0 libgtk2-gladexml-perl
  libwebkit1.0-cil libdatetime-format-w3cdtf-perl libxml-simple-perl
  nexuiz-data libmono-accessibility2.0-cil libggadget-1.0-0
  libdatetime-format-mail-perl libsexymm2 libdatetime-timezone-perl
  libemail-mime-encodings-perl liblist-moreutils-perl libclass-singleton-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kcm-gtk-kde4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,949kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 271710 files and directories currently installed.)
Removing kcm-gtk-kde4 ...
cd: 2: can't cd to /usr/share/kubuntu-default-settings/
dpkg: error processing kcm-gtk-kde4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kcm-gtk-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-laptop:~$

---

### Post by TheNessus on 2009-12-29
SOLVED it! by my self:P

I replaced the text of kcm-gtk-kde3.postrm to the text inside gnome-do.postrm, why gnome-do? because it's tried and tested, and not an unknown program by comparison.

removed the bloody thing worked, thank god.

---

