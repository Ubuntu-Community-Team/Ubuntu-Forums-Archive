---
title: "Failed to download repository information"
date: 2010-12-12
forum: General Help
---

### Post by Psrj on 2010-12-12
When ever I try to update Ubuntu I get the error "Failed to download repository information"
It tells me to check my internet connection.

The details say
W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I tried sudo apt-get clean and then sudo apt-get update but that didn't work either.  Any ideas?

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

404 Error means that the Server for Sun's Launchpad PPA is either down or no longer available or even, the address is not correct.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable the launchpad PPAs. Then Applications > Accessories > Terminal:

```
sudo apt-get update
```

---

### Post by Seankn on 2010-12-12
I have the Same Problem... I did what you told me... but Will it still update ubuntu software?

---

### Post by sikander3786 on 2010-12-12
> **Seankn said:**
> I have the Same Problem... I did what you told me... but Will it still update ubuntu software?
Obviously it won't. But it wasn't updating it before disabling either as the Server was unreachable.

Anyways, make sure you disabled only the offensive Software Sources/PPAs and not something else.

---

### Post by plucky on 2010-12-13
> **Psrj said:**
> When ever I try to update Ubuntu I get the error "Failed to download repository information"
It tells me to check my internet connection.

The details say
W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I tried sudo apt-get clean and then sudo apt-get update but that didn't work either.  Any ideas?

This is the repository that gives the 404 error```
http://ppa.launchpad.net/sun-java-community-team/sun-java64/ubuntu/dists/maverick/main/source/Sources.gz
```

This is what you want ```
http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/maverick/main/source/Sources.gz
```

Notice the difference between sun-java6 and sun-java64.

You need to change the .list file in /etc/apt/sources.list/d directory.

Please post output of ```
ls -l /etc/apt/sources.list.d/
```

---

