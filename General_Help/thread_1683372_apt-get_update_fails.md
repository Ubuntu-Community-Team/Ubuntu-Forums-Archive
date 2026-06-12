---
title: "apt-get update fails"
date: 2011-02-07
forum: General Help
---

### Post by isaas on 2011-02-07
hello everyone,
i'm having difficulties updating my system from terminal window.
when i type: sudo apt-get update, i get lots of messages like this one:

Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-security/multiverse Sources
  404  Not Found
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-security/main i386 Packages
  404  Not Found
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-security/restricted i386 Packages
  404  Not Found
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-security/universe i386 Packages
  404  Not Found
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-security/multiverse i386 Packages
  404  Not Found

however, when i do it using update manager, i don't have the same problem, it updates normally...

i tried changing repositories but no luck.

i'm running ubuntu 10.10 32-bit

any help is appreciated.

---

### Post by isaas on 2011-02-08
bump

---

### Post by gmargo on 2011-02-08
Security updates for active releases come from security.ubuntu.com, not the archive mirror sites.  The following should be in your **/etc/apt/sources.list** (added spacing for clarity):
```

deb     http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb     http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb     http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

---

### Post by isaas on 2011-02-10
thanks for your reply gmargo.
here's what happens when i change to main server:
```
Imposible obtener http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz  404  Not Found
Imposible obtener http://archive.canonical.com/dists/maverick/partner/binary-i386/Packages.gz  404  Not Found
Imposible obtener http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  404  Not Found
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz  403  Forbidden [IP: 74.125.43.99 80]
Imposible obtener http://dl.google.com/linux/earth/deb/dists/stable/main/binary-i386/Packages.gz  403  Forbidden [IP: 74.125.43.99 80]
Imposible obtener http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages.gz  403  Forbidden [IP: 74.125.43.147 80]
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```

i have an active internet connection, no proxies, and this is really confusing and frustrating... 

btw, when i use lines that you told me to use, i get the same message:

```
W: Imposible obtener http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  404  Not Found

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

```

---

### Post by gmargo on 2011-02-10
I tried getting two of those at random with wget and had no problem.  There's something else going on.  Can you fetch them manually?
```

$ wget http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz
$ wget http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz 
```

---

### Post by Kereltis on 2011-02-12
apt-get update is also failing for me as well as update manager and synaptic.

I get the following lines at the end when I try apt-get update:


W: Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Update manager says:

Failed to download repository information

W:Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Synaptic says:

Could not download all repository indexes

Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any help would be appreciated, I hope I won't have to reinstall my system.

---

### Post by plucky on 2011-02-12
> **Kereltis said:**
> apt-get update is also failing for me as well as update manager and synaptic.

I get the following lines at the end when I try apt-get update:


W: Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Update manager says:

Failed to download repository information

W:Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Synaptic says:

Could not download all repository indexes

Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any help would be appreciated, I hope I won't have to reinstall my system.


Remove that PPA from your software sources as there isn't a repository for "Maverick" only for "Lucid"

See [Here](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/)

Good Luck

---

### Post by Kereltis on 2011-02-12
> **plucky said:**
> Remove that PPA from your software sources as there isn't a repository for "Maverick" only for "Lucid"

See [Here](http://ppa.launchpad.net/speed-dreams/ppa/ubuntu/dists/)

Good Luck

That worked, thanks a lot. :)

---

### Post by isaas on 2011-02-13
yes, fetching them manually works like a charm, but for some reason apt-get and update manager don't... it's as if they didn't have internet connection, but that sounds absurd, because they're root owned...
```
-rwxr-xr-x 1 root   root      141596 2010-10-05 16:09 apt-get
```
and another thing, i haven't been able to update the system for 10 days now.
i tried installing new software, but neither synaptic nor apt-get allow it.

---

### Post by initialhit on 2011-02-13
Worst comes to worst... could always use alternate package managers such as YUM!

---

### Post by gmargo on 2011-02-13
> **initialhit said:**
> Worst comes to worst... could always use alternate package managers such as YUM!

While I'm pretty sure initialhit said this in jest, I want to stress to isaas - **_do not_** attempt to use **yum**.  That is an rpm package manager and is unsuitable for debian archives.  (Besides, how would you install it?)

isaas, since you can manually fetch those packages, this is a configuration or proxy issue.

Do you have an network proxy configured?  And what did you change 10 days ago?

---

### Post by isaas on 2011-02-13
gmargo, good question, i have no idea... i don't use proxy and i haven't changed anything related to my internet connection, that's for sure, and as for other changes, i would say nothing, and i would say it's an ubuntu issue, but since noone had similar problem, i'm sure i did something wrong. 
i think that i'll finally "solve" this problem by reinstalling ubuntu, since i lack better ideas... i know it's not the best way to solve issues like this, but it seems to be the easiest way

---

### Post by khanzada on 2011-02-26
**Failed to download repository information**
Sir i am getting this message from quite sometime. i am a new user of UBUNTU 10.04.1. now i can not update my OS. please help me through.


Thanks

---

### Post by isaas on 2011-02-26
sorry, i was a bit brutal and what i did was to reinstall the os, and i'm not sure that's the cleanest solution possible... but for the moment, that's the only one i can offer. good luck!

---

