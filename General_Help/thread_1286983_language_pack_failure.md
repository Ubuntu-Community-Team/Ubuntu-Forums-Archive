---
title: "language pack failure"
date: 2009-10-09
forum: General Help
---

### Post by seubill on 2009-10-09
Trying to install language-pack-kde-pt and error returns.

```
bill@E510:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  language-pack-kde-pt
The following NEW packages will be installed:
  language-pack-kde-pt
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/1945kB of archives.
After this operation, 7361kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170250 files and directories currently installed.)
Unpacking language-pack-kde-pt (from .../language-pack-kde-pt_1%3a9.04+20090803.2_all.deb) ...
Replacing files in old package language-pack-kde-pt-base ...
dpkg: error processing /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb (--unpack):
 trying to overwrite `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-pt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any help appreciated.

---

### Post by seubill on 2009-10-10
bump

---

### Post by arrange on 2009-10-10
You can try [overwriting the old files with the package]("http://shreevatsa.wordpress.com/2006/04/16/dpkg-error-trying-to-overwrite-x-which-is-also-in-package-y/").

---

### Post by seubill on 2009-10-10
Tried the force overwrite command and returned this:


```
bill@E510:~$ sudo dpkg -i --force-overwrite language-pack-kde-pt_1%3a9.04+20090803.2_all.deb
dpkg: error processing language-pack-kde-pt_1%3a9.04+20090803.2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 language-pack-kde-pt_1%3a9.04+20090803.2_all.deb

```

---

### Post by seubill on 2009-10-10
Tried to install the dependency package and will not download:

```
bill@E510:~$ sudo apt-get install language-pack-kde-pt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  language-pack-kde-pt
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

---

### Post by arrange on 2009-10-10
> **seubill said:**
> Tried the force overwrite command and returned this:


```
bill@E510:~$ sudo dpkg -i --force-overwrite language-pack-kde-pt_1%3a9.04+20090803.2_all.deb
dpkg: error processing language-pack-kde-pt_1%3a9.04+20090803.2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 language-pack-kde-pt_1%3a9.04+20090803.2_all.deb

```
Please read the link again. You should give the full path to the file */var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb*. Also make sure *Synaptic* and other package management applications are closed.

---

### Post by seubill on 2009-10-10
Thanks, I did have Synaptic open, but have closed it and re-ran the overwrite command this time with the full path.  Still dealing a bit of a fit:


```
bill@E510:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb
(Reading database ... 170250 files and directories currently installed.)
Unpacking language-pack-kde-pt (from .../language-pack-kde-pt_1%3a9.04+20090803.2_all.deb) ...
Replacing files in old package language-pack-kde-pt-base ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-pt
dpkg: dependency problems prevent configuration of language-pack-kde-pt:
 language-pack-kde-pt depends on language-pack-kde-pt-base (>= 1:9.04+20090413); however:
  Package language-pack-kde-pt-base is not configured yet.
dpkg: error processing language-pack-kde-pt (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 language-pack-kde-pt

```

---

### Post by seubill on 2009-10-10
Maybe I have it now


```
bill@E510:~$ sudo apt-get install language-pack-kde-pt-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
language-pack-kde-pt-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up language-pack-kde-pt (1:9.04+20090803.2) ...
Setting up language-pack-kde-pt-base (1:9.04+20090413.1) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.

```

---

