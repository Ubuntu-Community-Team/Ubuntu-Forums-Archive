---
title: "Beginner here with update problems"
date: 2011-08-30
forum: General Help
---

### Post by dmfagan9 on 2011-08-30
Hi All-

So I have an old Ubuntu (8.10 but i am not sure if its 32 or 64- if someone could let me know how I can figure this out it would be great!)

I routinely get update messages that do not go through. it says 'could not apply changes! fix brokn packages first!'

It also says upgrade to 9.04 is avaliable! (Of course there are higher ones as well- but this is what comes up)

When I go to update packages I receive this

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

any help would be much much appreciated!

Dylan

---

### Post by seawolf167 on 2011-08-30
Support for all versions up to and including 9.10 has been discontinued as they have reached their end of life. See [here ]("https://wiki.ubuntu.com/Releases")for the specific dates and versions. You'll want to upgrade (with a fresh installation) to either 10.04.3 LTS or the current incarnation, 11.04.

You won't have any update/upgrade problems with a currently supported version.

To find if x86 or x86_64, you can type in the following command

```
uname -a
```then take a look at the text just before the "GNU/Linux" part, something like i686 will be a 32 bit machine, and x86_64 will be a 64 bit machine

---

### Post by Enigmapond on 2011-08-30
You won't be able to update anything on your distro. It died some time ago and so did 9/10. The only way to solve your issues is to back up your important data and do a _fresh install_ of either 10.04 (I recommend) or 11.04. Good Luck!

---

### Post by Topsiho on 2011-08-30
Version 8.10 is more than 18 months old, and is not supported anymore.

So you can't find updates for it in the repositories.
You should install a newer version: 10.04 LTS (supported 3 years, until April 2013), or the newest version 11.04 (supported 18 months, until, ehm, where is my calculator :) ).

LTS versions (6.06, 8.04, 10.04, and probably 12.04 etc) are stable, well tested versions, with not the very newest software, and are supported for 3 years (desktop, server: 5 years), while the other versions are more state of the art, less reliable, and only supported for 18 months.

So your choice: install Ubuntu 10.04 (download newest version, I think 10.04.3), or 11.04.

Topsiho

---

### Post by seawolf167 on 2011-08-30
Here are some links that may help you out.

The 10.04 [install guide]("https://help.ubuntu.com/10.04/installation-guide/index.html"), 11.04 [install guide]("https://help.ubuntu.com/11.04/installation-guide/index.html"), [download link]("http://www.ubuntu.com/download/ubuntu/download"), general [install guide]("https://help.ubuntu.com/community/Installation"), 10.04 [documentation]("https://help.ubuntu.com/10.04/"), 11.04 [documentation]("https://help.ubuntu.com/11.04/").

---

