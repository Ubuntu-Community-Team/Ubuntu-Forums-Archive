---
title: "apt-get cant resolve/find source"
date: 2009-07-23
forum: General Help
---

### Post by kameelperdza on 2009-07-23
:confused:Hi im trying to update my ubuntu.
 
But im getting this error.
 
Have the site moved or is the server down?
 
[EMAIL="root@Apie"]root@Apie[/EMAIL]:~# apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty/main Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty/restricted Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty/universe Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty/multiverse Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates Release.gpg
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates/main Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates/restricted Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates/universe Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_ZA
  Could not resolve 'za.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2)  Could not resolve 'za.archive.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by kpkeerthi on 2009-07-23
Firefox reports file not found (404) when I tried to open those with it (Try clicking on the last URL in your post).

Switch to a different mirror or Main site from System -> Admin -> Software Sources.

---

### Post by kameelperdza on 2009-07-23
im running ubuntu server 9.04.
 
How can i change the mirror?

---

### Post by kameelperdza on 2009-07-23
i edited /etc/apt/sources.list and changed it za.arhive.ubuntu.com to uk.arhive.ubuntu.com

---

### Post by SecretCode on 2009-07-23
I'm also finding that za.archive.ubuntu.com is down. 

How do we find the contact for the mirror site?

---

### Post by kameelperdza on 2009-07-23
maybe they are experiencing server problems. I have updated my server by usung the uk one.

---

