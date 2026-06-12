---
title: "webmin module not supporting"
date: 2012-04-27
forum: General Help
---

### Post by Rakeshvijayan on 2012-04-27
Hi friends I had installed and configure dansguradian on ubuntu 11.10 and I installed webmin to configure 
the dansguradian ,I got message when I opened the dansguardian server on webmin here is the message 


[

[COLOR=brown]Warning - DansGuardian binary file not found,  maybe you need to update your [module config]("https://kak:10000/config.cgi?dansguardian") (especially the directory paths).
(Expected location: /sbin/dansguardian)[/COLOR]
 
[COLOR=brown]Warning - the version of DansGuardian you have is not supported by this Webmin module version
Webmin Module Version 0.7.1 supports DG version 2.10 (& 2.9)
Currently installed DG version ?[/COLOR]
 
[COLOR=brown]Warning - running as root(superuser) may cause new files to be innaccessible by production DansGuardian

]


[COLOR=Black]what should i do next ,were should I get the exact module, I had search in google but no result found if any one know the solution please help me to set up dansguardian module on webmin 

I installed dansguardian verion is 


kajf@kak:~$ sudo dpkg -s dansguardian 
[sudo] password for kajf: 
Package: dansguardian
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 2376
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2.10.1.1-3ubuntu1
Depends: libc6 (>= 2.4), libclamav6 (>= 0.97.2+dfsg), libgcc1 (>= 1:4.1.1), libpcre3 (>= 8.10), libstdc++6 (>= 4.6), zlib1g (>= 1:1.1.4), perl, adduser, clamav (>= 0.80)

[/COLOR][/COLOR]

---

### Post by Rakeshvijayan on 2012-04-28
any solution

---

