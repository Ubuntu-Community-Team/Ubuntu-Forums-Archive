---
title: "can't install CURL err"
date: 2009-09-10
forum: General Help
---

### Post by venomm on 2009-09-10
[php]root@ubuntu:/home/ubuntu# apt-get install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 197kB of archives.
After this operation, 311kB of additional disk space will be used.
Err http://security.ubuntu.com hardy-security/main curl 7.18.0-1ubuntu2.1
  404 Not Found
Err http://archive.ubuntu.com hardy-updates/main curl 7.18.0-1ubuntu2.1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.18.0-1ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/php]

---

### Post by NoaHall on 2009-09-10
The site doesn't exist...

get from here - [http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)

---

