---
title: "LibreOffice Package Errors"
date: 2011-10-12
forum: General Help
---

### Post by AdamShumpisxXx on 2011-10-12
I switched from Xubuntu to Ubuntu (11.04 on both) due to problems with Thunar being the worst file manager in any *buntu variant I have ever come across. To replace it I went to this link:

```
http://www.psychocats.net/ubuntu/puregnome
```

An ran the code underneath "Remove Xubuntu". Everything seemed to work perfectly and does work perfectly until I tried to run:

```
sudo apt-get autoremove
```

I got this in return:

```
USER@COMPUTER:~$ sudo apt-get autoremove
[sudo] password for USER: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:3.3.4) but it is not installed
E: Unmet dependencies. Try using -f.

```

When I try to run the command it gives me I get back:

```
USER@COMPUTER:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqca2 cdparanoia libdiscid0 oxygen-icon-theme
  libqt4-sql-mysql docbook-xsl shared-desktop-ontologies libflac++6
  mysql-common libntrack-qt4-1 virtuoso-minimal k3b-data libqt4-xmlpatterns
  libsoprano4 libqapt1 kdelibs5-data libvirtodbc0 libgif4 icoutils
  libthreadweaver4 libntrack0 libqt4-sql libstreamanalyzer0 libkntlm4
  libmysqlclient16 libattica0 libkjsapi4 libstreams0
  virtuoso-opensource-6.1-common libqt4-script libssh-4 libaudio2
  soprano-daemon kdebase-runtime-data libreadline5 libiodbc2 libmpcdec6
  virtuoso-opensource-6.1-bin ntrack-module-libnl-0 libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 16.8 MB of archives.
After this operation, 43.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-common all 1:3.3.4-0ubuntu1 [16.8 MB]
Fetched 16.8 MB in 33s (494 kB/s)                                              
(Reading database ... 151543 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.3.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Can't open /usr/share/applications/openoffice.org3-base.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-calc.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-draw.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-impress.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-javafilter.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-math.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-printeradmin.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-startcenter.desktop: No such file or directory at -e line 1, <> line 1951.
Can't open /usr/share/applications/openoffice.org3-writer.desktop: No such file or directory at -e line 1, <> line 1951.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.3.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This now turns into an infinite cycle and I can't install anything either through the terminal or Ubuntu Software Center. What do I do? Is it something simple or did I screw the pooch on this one? Thank you in advance for helping!

---

### Post by rattskjelke on 2011-10-12
I had something similar happen about a year ago.
Reinstalling ubuntu-desktop fixed it.

---

### Post by AdamShumpisxXx on 2011-10-13
Yeah, that's not going to happen. What I did is type in:

```
sudo apt-get autoremove
```

...and look at all the broken dependencies and files and force remove them all and purge their configurations until:

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

...came back clean. Now everything works perfectly! I will give you the two commands I used tomorrow when I'm back in the office. I'll mark this as solved after then so somebody can get some use out of this.

---

### Post by AdamShumpisxXx on 2011-10-14
The commands are as follows:

```
sudo dpkg -r --force-depends ??? (package name)
```

...for every package I saw when I ran "autoremove". Then this command:

```
sudo dpkg --purge ??? (package name)
```

...to remove the rest of it. Then I ran "autoremove" and "autoclean" until it all came back clean. So, there you have it!

:KS

---

