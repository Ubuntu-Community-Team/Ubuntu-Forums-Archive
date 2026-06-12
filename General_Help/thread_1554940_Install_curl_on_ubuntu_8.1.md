---
title: "Install curl on ubuntu 8.1"
date: 2010-08-17
forum: General Help
---

### Post by surfsup00 on 2010-08-17
Having real trouble installing curl on my LAMP server. Sorry if i am just being real dim here

Using 

> sudo apt-get install curl libcurl3 libcurl3-dev php5-curland getting

> Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libcurl3 7.18.2-1ubuntu4.3
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libcurl3 7.18.2-1ubuntu4.3
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main curl 7.18.2-1ubuntu4.3
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main php5-curl 5.2.6-2ubuntu4.1
  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.3_i386.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.18.2-1ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.18.2-1ubuntu4.3_i386.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.1_i386.deb)  404 Not Found [IP: 91.189.88.37 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by xangua on 2010-08-17
ubuntu 8.10 intrepid ibex is no longer supported, get lucid :)

ubuntu.com

---

### Post by surfsup00 on 2010-08-20
ok

---

### Post by surfer on 2010-08-20
intrepid is indeed no longer supported, but if you dont want to upgrade, change your [FONT="Courier New"]/etc/apt/sources.list[/FONT] entries to

```
http://old-releases.ubuntu.com/
```

---

### Post by surfsup00 on 2010-08-25
Hi thanks

I tried your suggestion and now i get

```
E: Type âhttp://old-releases.ubuntu.com/â is not known on line 38 in source list /etc/apt/sources.list


E: The list of sources could not be read.
```

---

### Post by surfsup00 on 2010-08-25
figured i'd stick the lot in you can tell me where i am going wrong

> 
#deb [http://213.171.201.6/intrepid-test/](http://213.171.201.6/intrepid-test/) intrepid main

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)  intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)  intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)  intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)  intrepid-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)  intrepid universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
deb-src [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
deb [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/) apt-mirror/
deb-src [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)


---

### Post by gmargo on 2010-08-25
I think you just need an "apt-get update" before trying to install **curl** - your attempt tried to install version "7.18.2-1ubuntu4.3" but the current version is "7.18.2-1ubuntu4.4".

Remove the last 4 lines of the /etc/apt/sources.list file and do an "apt-get update" (or "aptitude update") and you should be fine.  Ignore that old-releases stuff.  While 8.10 Intrepid no longer receives security updates, the package lists and packages, including curl, still live in the normal archive directories.

---

