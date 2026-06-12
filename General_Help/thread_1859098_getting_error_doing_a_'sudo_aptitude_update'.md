---
title: "getting error doing a 'sudo aptitude update'"
date: 2011-10-13
forum: General Help
---

### Post by ryadav on 2011-10-13
when I do a 'sudo aptitiude update', the following error just showed up today? I did not alter my package repository settings.

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en             
Fetched 199 B in 8s (25 B/s)                                                       
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I know kubuntu 11.10 was release a few days ago, would this have anything to do with the error I am seeing?

uname -a
Linux karma 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ryadav on 2011-10-13
I am also seeing the same error using the synaptic package manager when I click on 'Reload', or do a 'sudo apt-get update'

Note: I have done, 'sudo aptitude autoclean' and 'sudo aptitude clean'

more errors:

Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en            
Fetched 1,061 kB in 11s (94.6 kB/s)                                               
W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2011-10-13
This worked for me on Oneiric:

```
sudo aptitude autoclean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo aptitude autoclean

sudo aptitude update
```

(Thanks to dino99.)

---

### Post by ryadav on 2011-10-15
Hi thanks for the help, but it seems the problem just went away on it's own.

---

