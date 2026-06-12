---
title: "Problems with 9.10 (Funny noises and updates)"
date: 2009-12-11
forum: General Help
---

### Post by indrulz on 2009-12-11
Hi everyone
I recently upgraded from 9.04 to 9.10. After the installation the first problem I faced was the funny background noise. A strong burpy noise when I plug in my headphones. The sound continous with a 5 second interval until I play something (Audio or Video).

The second problem I noticed was with updates, after downloading the packages it gives me this problem :



An error occured:
Below are the details 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 81.171.111.247 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.




Any help will be hugely appreciated.


Cheers

---

### Post by ubudog on 2009-12-11
Are you connected to the internet?

---

### Post by indrulz on 2009-12-11
Oh well, the sound problem is now sorted (Sorry, didn't look at the other thread which explains everything about noise) but the updating problem is still there

---

### Post by ubudog on 2009-12-11
Do you have internet access?

---

### Post by indrulz on 2009-12-11
Yes, adsl2+

---

### Post by ubudog on 2009-12-11
Well, it's obviously not the internet connection.  Open up software sources and click on the tab named "Ubuntu Software." Make sure all the items are checked.

---

### Post by indrulz on 2009-12-11
Yes, everything is ticked. I have tried almost everything I could. Even the software sources do not reload.

---

### Post by indrulz on 2009-12-11
Synaptic package manager I meant

---

### Post by indrulz on 2009-12-11
Now it says it could not download all repositories. It downloaded some repositories and I have been able to download those updates. 
These are the repositories it could not download :


GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_AU.bz2)  
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_AU.bz2)  
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ubudog on 2009-12-13
Maybe you should reinstall.  Anyone else have an idea?

---

