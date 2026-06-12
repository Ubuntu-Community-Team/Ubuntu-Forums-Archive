---
title: "Repositories Gone Missing"
date: 2006-03-10
forum: General Help
---

### Post by BitTorrentBuddha on 2006-03-10
hey, I recently ran update and synaptic, both times i got ```
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
``` and these all came at once, this is different than most of the times because the actual files are missing from /var/lib/apt/lists, all that's in there is ```
archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packagesarchive.ubuntu.com_ubuntu_dists_breezy-backports_Release
archive.ubuntu.com_ubuntu_dists_breezy-backports_Release.gpg
archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packagesarchive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_Release
archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_universe_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy-updates_main_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy-updates_Release
archive.ubuntu.com_ubuntu_dists_breezy-updates_Release.gpg
archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_source_Sources
ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_source_Sources
ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_source_Sources
lock
partial
ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages
ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages
ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages
ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packageswine.sourceforge.net_apt_binary_Packages
wine.sourceforge.net_apt_binary_Release
``` I could be wrong but I always thought there were more than that.

---

### Post by tOpEzz on 2006-03-11
heyy... i also got the same problem... how to solve this problem... please let me know the solution man...

---

### Post by akiro.yamamoto on 2006-03-11
It seems the repos you want to use are unavailable..... or your conection is down ;)
If the first is true you can use this:
[ Ubuntu Source.lists Generator](http://www.ubuntulinux.nl/source-o-matic)
If the second is true post back here ;)

---

### Post by lamego on 2006-03-11
Did you hit the "Reload" button on synaptic ? This should reload the packages info...

---

### Post by s_spiff on 2006-03-11
exactly same problem! i was just about to start a new thread over the issue... lusckily saw this thread...seems like the repo is down! :(

---

### Post by entryname on 2006-03-12
Sorry chums but I don't think this is the repos, or at least not always :neutral: 

I've had what looks to be the same problem, I think twice but might be three times. The scenario goes something like this: leave update manager and synaptic alone for a while, say two or three days, including for example when the updates icon is up. 

You may find the update icon mysteriously vanishes without doing any updates. If you start it, it will deny there are any updates even though there were several two or three days before, and you haven't done any. On the other hand, start synaptic and you then get an error message saying it couldn't source this and that - the same as it would say if you weren't on line at the time (or I guess if all the repositories were down).

You can reload either from the update manager or synaptic, and that will appear to fix the problem. The repos that were supposedly offline are now magically back online..... until the next time the problem occurs. I'm not sure what is triggering this but I suspect a bug somewhere. Suggestions?? :-k

---

### Post by BitTorrentBuddha on 2006-03-20
after refreshing i get this, ```
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
http://wine.sourceforge.net/apt/binary/Release.gpg: Temporary failure resolving 'wine.sourceforge.net'
http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg: Temporary failure resolving 'security.ubuntu.com'
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/Release.gpg: Temporary failure resolving 'ubuntu-backports.mirrormax.net'
http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)

```
followed by the same error
```
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

---

### Post by BitTorrentBuddha on 2006-03-22
I used the auto-sources.list maker and all the repos came back as no file found for it in /var/lib/apt/lists/, I think it's something on my machine that's wrong

---

### Post by BitTorrentBuddha on 2006-03-23
bump, can anyone tell me how to replace the physical files if that's the problem? this is from apt-get update ```
Ign http://deb.opera.com etch Release.gpg
Ign http://deb.opera.com etch Release
Ign http://deb.opera.com etch/non-free Packages
Ign http://deb.opera.com etch/non-free Packages
Get:1 http://deb.opera.com etch/non-free Packages [639B]
98% [1 Packages gzip 0] [Connecting to archive.ubuntu.com] [Connecting to packa
gzip: stdin: not in gzip format
Err http://deb.opera.com etch/non-free Packages
  Sub-process gzip returned an error code (1)
Get:2 http://deb.opera.com etch/non-free Packages [639B]
99% [Connecting to archive.ubuntu.com] [Connecting to packages.freecontrib.org]
gzip: stdin: not in gzip format
Err http://deb.opera.com etch/non-free Packages
  Sub-process gzip returned an error code (1)
Ign http://packages.freecontrib.org breezy Release.gpg
Ign http://packages.freecontrib.org breezy Release
Ign http://packages.freecontrib.org breezy/free Packages
Ign http://packages.freecontrib.org breezy/non-free Packages
Hit http://packages.freecontrib.org breezy/free Packages
Hit http://packages.freecontrib.org breezy/non-free Packages
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [27.0kB]
Ign http://wine.sourceforge.net binary/ Release.gpg
Get:5 http://security.ubuntu.com breezy-security/main Packages [44.4kB]
Get:6 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:7 http://security.ubuntu.com breezy-security/main Sources [13.6kB]
Get:8 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:9 http://security.ubuntu.com breezy-security/universe Packages [31.1kB]
Get:10 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages
Get:11 ftp://ftp.free.fr breezy Release.gpg
Ign ftp://ftp.free.fr breezy Release.gpg
Get:12 ftp://ftp.free.fr breezy Release
Ign ftp://ftp.free.fr breezy Release
Get:13 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:14 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Get:15 ftp://ftp.free.fr breezy/free Sources [316B]
Get:16 ftp://ftp.free.fr breezy/non-free Sources [473B]
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Get:17 http://ubuntu-backports.mirrormax.net breezy-extras/main Packages [33B]
Get:18 http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages [33B]
Get:19 http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages [33B]
Get:20 http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages [33B]
Get:21 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:22 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:23 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:24 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Get:25 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Get:26 http://archive.ubuntu.com breezy-updates/main Packages [36.0kB]
Get:27 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:28 http://archive.ubuntu.com breezy-updates/main Sources [17.5kB]
Get:29 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:30 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Get:31 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:32 http://archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:33 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Fetched 274kB in 1m6s (4111B/s)
Failed to fetch http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by BitTorrentBuddha on 2006-03-24
bump :(

---

