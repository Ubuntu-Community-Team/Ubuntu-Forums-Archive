---
title: "Can install packages from the respository."
date: 2011-02-26
forum: General Help
---

### Post by Cityscape on 2011-02-26
Hi, I just installed OpenGEU Luna Serena (based on Ubuntu 8.10). Internet works, I'm using it now. But it seems like the package managers can't access the internet because they fail to get packages. Here are the error messages I'm receiving...

Synaptic
```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://greenie.sk/ubuntu/dists/intrepid/e17/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://greenie.sk/ubuntu/dists/intrepid/opengeu/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
Add/Remove Applications: (when trying to install amoroc)
```

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

(it downloaded few of the packages before giving me this message, when it did give me the messages I chose no)

An error occurred

The following details are provided:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.10-0ubuntu3_i386.deb
  404 Not Found [IP: 91.189.88.40 80]

```

So some packages seem to download and others don't, I'm confused....please help.

---

### Post by Topsiho on 2011-02-26
Ubuntu 8.10 is older than 18 months, so it is not supported anymore.

Topsiho

---

### Post by Cityscape on 2011-02-26
> **Topsiho said:**
> Ubuntu 8.10 is older than 18 months, so it is not supported anymore.

Topsiho
So it is not possible to download and install packages on 8.10 then?

---

### Post by sikander3786 on 2011-02-26
> **Cityscape said:**
> So it is not possible to download and install packages on 8.10 then?
You can still access the repositories. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html](http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html)

However you won't be getting any updates, security patches so it is recommended that you upgrade immediately to a current release.

---

### Post by Topsiho on 2011-02-26
Ha, thank you for this information, did not know this.

Anyhow, just like sikander 3786 said, if you use the internet it is not wise to use a discontinued distribution.

You could better use the latest Ubuntu LTS version, 10.04.2 (the second "service pack", 17 Feb 2011), of which the desktop will be supported until April 2013 (LTS versions are supported 3 years on the desktop, 5 years on servers).

Topsiho

---

