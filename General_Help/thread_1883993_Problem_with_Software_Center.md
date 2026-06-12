---
title: "Problem with Software Center"
date: 2011-11-20
forum: General Help
---

### Post by Ventris56 on 2011-11-20
Hi,

When I run Software Center I get this message:

Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

The repair fails and these are the details:

```

InstallArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 136447 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_20090808ubuntu26_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu26_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libgnome-keyring.so.0.1.1', which is also in package libgnome-keyring0-ia32 3.2.0-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_20090808ubuntu26_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of libgnome-keyring0-ia32:
 libgnome-keyring0-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libgnome-keyring0-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbz2-1.0-ia32:
 libbz2-1.0-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libbz2-1.0-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-ia32:
 libc6-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libc6-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatk1.0-dbg-ia32:
 libatk1.0-dbg-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libatk1.0-dbg-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxtst6-ia32:
 libxtst6-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libxtst6-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcurl4-gnutls-dev-ia32:
 libcurl4-gnutls-dev-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libcurl4-gnutls-dev-ia32 (--configure):
 dependency problems - leaving unconfigured

```

Help with this would be much appreciated as it is driving me nuts.

---

### Post by Rubi1200 on 2011-11-20
Hi and welcome to the forums :)

Open a terminal with Ctrl+Alt+T and run the following commands one at a time and post back with error messages (if any):

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

---

### Post by Ventris56 on 2011-11-20
sudo apt-get install -f

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libatk1.0-dbg-ia32 : Depends: ia32-libs but it is not installed
 libbz2-1.0-ia32 : Depends: ia32-libs but it is not installed
 libc6-ia32 : Depends: ia32-libs but it is not installed
 libcurl4-gnutls-dev-ia32 : Depends: ia32-libs but it is not installed
 libgnome-keyring0-ia32 : Depends: ia32-libs but it is not installed
 libxtst6-ia32 : Depends: ia32-libs but it is not installed
E: Unmet dependencies. Try using -f.

```

sudo dpkg --configure -a

```

dpkg: dependency problems prevent configuration of libgnome-keyring0-ia32:
 libgnome-keyring0-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libgnome-keyring0-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbz2-1.0-ia32:
 libbz2-1.0-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libbz2-1.0-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-ia32:
 libc6-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libc6-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatk1.0-dbg-ia32:
 libatk1.0-dbg-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libatk1.0-dbg-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxtst6-ia32:
 libxtst6-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libxtst6-ia32 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcurl4-gnutls-dev-ia32:
 libcurl4-gnutls-dev-ia32 depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing libcurl4-gnutls-dev-ia32 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome-keyring0-ia32
 libbz2-1.0-ia32
 libc6-ia32
 libatk1.0-dbg-ia32
 libxtst6-ia32
 libcurl4-gnutls-dev-ia32

```

sudo apt-get update

```

Ign http://security.ubuntu.com oneiric-security InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Ign http://archive.ubuntu.com oneiric InRelease      
Ign http://archive.ubuntu.com oneiric-updates InRelease
Hit http://security.ubuntu.com oneiric-security Release
Hit http://archive.ubuntu.com oneiric Release.gpg
Get:1 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Get:2 http://archive.ubuntu.com oneiric-updates Release [32.4 kB]
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/main amd64 Packages
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric/main i386 Packages
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Get:3 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [155 kB]
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Get:4 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,966 B]
Get:5 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [43.1 kB]
Get:6 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [3,211 B]
Get:7 http://archive.ubuntu.com oneiric-updates/main i386 Packages [155 kB]
Get:8 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:9 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [43.4 kB]
Get:10 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [3,840 B]
Get:11 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:12 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:13 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:14 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Get:15 http://archive.ubuntu.com oneiric-updates/main Translation-en [77.5 kB]
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:16 http://archive.ubuntu.com oneiric-updates/universe Translation-en [27.3 kB]
Fetched 547 kB in 2s (247 kB/s)                                     
Reading package lists... Done

```

---

### Post by Paddy Landau on 2011-11-21
Looking at the error messages, try the following commands. If you get an error, stop and post back here.
```
sudo apt-get --fix-broken install ia32-libs
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ventris56 on 2011-11-21
Hi Paddy, errors from the first one.

sudo apt-get --fix-broken install ia32-libs

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 238 not upgraded.
6 not fully installed or removed.
Need to get 0 B/30.1 MB of archives.
After this operation, 118 MB of additional disk space will be used.
(Reading database ... 136447 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_20090808ubuntu26_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu26_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libgnome-keyring.so.0.1.1', which is also in package libgnome-keyring0-ia32 3.2.0-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_20090808ubuntu26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Paddy Landau on 2011-11-21
I'm sorry; at this point I do not know what to do next.

Are you using [s]Natty[/s] Oneiric 11.10?

---

### Post by Ventris56 on 2011-11-21
No worries, Paddy. I'm running Ubuntu 11.10 (Oneiric Ocelot).

---

### Post by Paddy Landau on 2011-11-21
Sorry, yes, I meant Oneiric 11.10. Silly me.

If it's a reasonably new installation, you may find it easier to reinstall (back up your data first!), unless someone can answer your question.

---

### Post by Ventris56 on 2011-11-21
Yes, I was also thinking a reinstall might be the easiest option. It is a fairly new installation so not too much of a  headache.

---

### Post by Ventris56 on 2011-11-21
Reinstalled and all is well :)

---

### Post by Paddy Landau on 2011-11-22
Good, I'm glad you have it solved.

---

