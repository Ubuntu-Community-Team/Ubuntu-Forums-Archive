---
title: "program install issues, need to uninstall or fix"
date: 2006-02-13
forum: General Help
---

### Post by PDXlewis on 2006-02-13
hey there,
 I am slowly but surelygetting around in ubuntu. just learned about apt-get. whooo hoooo. 

what I really want to do is install k3b on ubuntu  (and I've done that on another load of ubuntu at work). but I get an error that I think stems from my attempt (failed) to install realplayer.  If I try to apt-get install anything now or even just start up synaptic I get this error:

"E: The package realplayer needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

So i am not sure how to go about fixing this. Can't find the archive or package info to uninstall in synaptic.

I tried to search on this error but no luck. I figure it is something I just haven't gotten to in my learning....

I'd like to just wipe out realplayer and try that later anyway but I really need to be able install things and I so like apt-get.

Any help?

Thanks
Tim

---

### Post by oakz on 2006-02-13
Try running the following command:

$ sudo apt-get -f update

If that doesn't clear up your apt-get problem, post the output from the command

---

### Post by PDXlewis on 2006-02-16
[QUOTE=oakz]Try running the following command:

$ sudo apt-get -f update

If that doesn't clear up your apt-get problem, post the output from the command[/QUOTE]


Ran the command and looks ok but still get error for realplayer install......
here is what I get with the above command:
 Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Fetched 4B in 2s (2B/s)
Reading package lists... Done

---

### Post by PDXlewis on 2006-02-19
All better, but it was from a reload. I found some other folks with similar problems but could never get any of their fixes to work. I will just be a little more careful when loading things willy nilly.

Thanks anyway
Tim:)

---

