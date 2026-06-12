---
title: "memtest86+ error"
date: 2006-04-27
forum: General Help
---

### Post by drhash on 2006-04-27
Hi,

I am a beginner with linux and I am having some difficulty trying to troubleshoot the error I have pasted below. I cannot install or update anything on my computer and I dont know a better place to start then here.Please HELP!!!

Error Message:

 E: /var/cache/apt/archives/libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb: unable to open files list file for package `memtest86+'

Terminal :

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb (--unpack):
 unable to open files list file for package `memtest86+': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb
Processing was halted because there were too many errors.


Many Thanks,

drhash

---

### Post by az on 2006-04-27
You either have a bad cd or hardware problems.

boot into recovery mode if you can and try

apt-get -f install

or
dpkg --config -a

if that runs fine do

apt-get install ubuntu-desktop

the last command makes sure everything is instaled.

---

