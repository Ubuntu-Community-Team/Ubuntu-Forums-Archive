---
title: "how to get KATE on UBUNTU"
date: 2010-01-31
forum: General Help
---

### Post by haarsh on 2010-01-31
hi all... im totally newbie here and also 4 UBUNTU too... i am running ubuntu on virtual machine (virtual Box)..but i have a BIG problem using KATE on UBUNTU....my version is 7.04.. i have tried several things to get KATE on my ubuntu....but failed. so plzz guys if u can guide me step by step to install kate on ubuntu...
very big help ..thnxx

---

### Post by haarsh on 2010-01-31
i tried sudo aptitude install kate 
sudo apt-get install kate

---

### Post by woodmaster on 2010-01-31
Try SciTE instead...

---

### Post by haarsh on 2010-01-31
> **woodmaster said:**
> Try SciTE instead...

bro.. can u plzz explain how can i do it...:( i don't know much how can i try SciTE ... plzz

---

### Post by woodmaster on 2010-01-31
Or get KDE desktop and install there...

---

### Post by woodmaster on 2010-01-31
install with synaptic Package Manager under System- Admin tab

---

### Post by haarsh on 2010-01-31
> **woodmaster said:**
> install with synaptic Package Manager under System- Admin tab

bro theres ERROR ...some sites are displayed saying cannot fetch

---

### Post by haarsh on 2010-01-31
:(

---

### Post by jbiggs12 on 2010-01-31
What's the output of the error that you get while trying to install Kate through Aptitude? (the sudo apt-get install command that you ran)

---

### Post by haarsh on 2010-01-31
> **jbiggs12 said:**
> What's the output of the error that you get while trying to install Kate through Aptitude? (the sudo apt-get install command that you ran)

i ran sudo apt-get install kate ...then it asks for confirmation... when pressd yeas ... some errors are displayed...
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libartsc0......
404 not found {IP:91.189.88.40 80]

like wise many errors come
finally it displays unable to fetch some archives , may be run apt-get update or try with fix missing :(

---

### Post by arnab_das on 2010-01-31
sudo apt-get install kate kate plugins

This will install Kate with all its plugins and dependencies.

(Off topic and no offence: great title! How to get Kate on Ubuntu :P sorry, bad joke. :) )

---

### Post by haarsh on 2010-01-31
> **arnab_das said:**
> sudo apt-get install kate kate plugins

This will install Kate with all its plugins and dependencies.

(Off topic and no offence: great title! How to get Kate on Ubuntu :P sorry, bad joke. :) )

hehe ... :):) bro.. tried it but doesn't work...[ sudo apt-get install kate kate-plugins ].. it says that cannot fetch some web sites... what do i need to get this done ...
some site says 
[B]Feisty update broken due to end-of-life
2009, January 20 - 01:55 &#8212; müzso
Feisty got its End-Of-Life statement and it also means that the official Feisty repository was moved from [http://archive.ubuntu.com/](http://archive.ubuntu.com/) to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/). If you don't know what's going on and just run apt-get update, you'll see error messages like this ...

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Fetched 3B in 0s (4B/s)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

To fix that, replace all references of archive.ubuntu.com with old-releases.ubuntu.com in your /etc/apt/sources.list and run update again.[/B]
but don't know how to do it @ all :(

---

### Post by jbiggs12 on 2010-01-31
Have you tried running sudo apt-get update?

---

### Post by jbiggs12 on 2010-01-31
Try this:

```
sudo gedit /etc/apt/sources.list
```

Save a backup of this file in case you mess something up, and then replace all of the archive.ubuntu.com's with old-releases.ubuntu.com (you can try a find-replace if you like.) Give that one a try, and then try sudo apt-get update.

---

### Post by haarsh on 2010-01-31
> **jbiggs12 said:**
> Try this:

```
sudo gedit /etc/apt/sources.list
```

Save a backup of this file in case you mess something up, and then replace all of the archive.ubuntu.com's with old-releases.ubuntu.com (you can try a find-replace if you like.) Give that one a try, and then try sudo apt-get update.

thnxx bro.. it's still updating ... after that can i install kate using sudo apt-get install kate

---

### Post by oldos2er on 2010-01-31
7.04 reached its end-of-life long ago, which is why its repositories are offline.

---

### Post by jbiggs12 on 2010-01-31
> **oldos2er said:**
> 7.04 reached its end-of-life long ago, which is why its repositories are offline.

Agreed... Are you able to update to a newer (or at least still supported) version of Ubuntu? Or are you on a PowerPC computer?

Edit: By the way, yes, you can try sudo apt-get install kate after you've updated. :)

---

### Post by gmargo on 2010-02-01
The Feisty 7.04 repositories are still online, but have been moved.

Change your /etc/apt/sources.list to point to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Be aware that Feisty no longer gets security updates.

---

### Post by dondiego2 on 2010-02-01
> **haarsh said:**
> hi all... im totally newbie here and also 4 UBUNTU too... i am running ubuntu on virtual machine (virtual Box)..but i have a BIG problem using KATE on UBUNTU....my version is 7.04.. i have tried several things to get KATE on my ubuntu....but failed. so plzz guys if u can guide me step by step to install kate on ubuntu...
very big help ..thnxx


Why not just use gedit?

---

