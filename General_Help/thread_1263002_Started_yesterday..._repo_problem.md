---
title: "Started yesterday... repo problem"
date: 2009-09-10
forum: General Help
---

### Post by misfitpierce on 2009-09-10
Anyone else having trouble updating repos?

13% [Connecting to us.archive.ubuntu.com (91.189.88.140)] [Connecting to securi

Mine is freezing there since yesterday...

Also this,

Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
  Unable to connect to security.ubuntu.com http:

---

### Post by misfitpierce on 2009-09-10
I'm the only one getting a repo error when updating sources on Ubuntu atm at that point?

---

### Post by drs305 on 2009-09-10
No, you aren't alone. At the moment I cannot connect to the Karmic security repository on any of the servers I tried. I unticked it in Synaptic and all the rest update normally.

---

### Post by misfitpierce on 2009-09-10
Ok was just checking if others having problems on security repo's atm.. I changed some sources last night so was making sure I didnt mess anything up. Thankyou for your reply.

---

### Post by earthpigg on 2009-09-10
this same thread exists several places on the forum right now :D

system -> administration -> software sources -> ubuntu software -> download from -> other -> select best server

---

### Post by misfitpierce on 2009-09-10
> **earthpigg said:**
> this same thread exists several places on the forum right now :D

system -> administration -> software sources -> ubuntu software -> download from -> other -> select best server

I thought it was working good till end... still says security one down on another server... so i'll just guess security one is down for now...

ex.
Get:32 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) jaunty-backports/universe Packages [10.2kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com http:
Fetched 9859kB in 2min 0s (82.1kB/s)                  
Reading package lists... Done
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by drs305 on 2009-09-10
I tried 6 servers around the world and none worked. We'll just have to wait for whatever is being done to be accomplished (or fixed ;-) ).

---

### Post by misfitpierce on 2009-09-10
Indeed :(

---

### Post by Fableflame on 2009-09-10
It's back up guys!
Updating!

---

