---
title: "Can't add repositories"
date: 2009-11-05
forum: General Help
---

### Post by infornography on 2009-11-05
I have installed 9.10 on three separate computers and have the same problem on them all. I add extra repositories by uncommenting them in sources.list. But when I run apt-get update I get this crap:

Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_AU          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_AU   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_AU 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic Release.gpg   
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates Release.gpg
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports Release.gpg
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-backports/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

So I can't install anything I don't already have. Help!

---

### Post by wilee-nilee on 2009-11-05
Have you tried going to software sources and ticking other in the 1st tab then best server it will ping all the ones listed and highlight the fastest one save and run update again.

---

### Post by garvinrick4 on 2009-11-05
You need a different ubuntu server or mirror there are 325 of them. Change to
different one in software sources  tab   ubuntu software  - Download from   -  Other

than pick a new one  or ping for best one.   After find a new one hit close it will reload new
repositorie's and toss out your bad ones. 

Have a nice day.

---

### Post by bibcuswi on 2009-11-05
thanks 4 ur help

---

