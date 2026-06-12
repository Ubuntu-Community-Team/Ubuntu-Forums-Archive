---
title: "i am not able to download any packages"
date: 2009-08-08
forum: General Help
---

### Post by vivek shekar on 2009-08-08
Dear friends,

i am using ubunthu 7.04. now a days i am not able to donload any packegs i am geting errors like this....


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]

help me...

---

### Post by credobyte on 2009-08-08
Edgy is no longer supported ( dead ). You should upgrade your OS to 8.04 LTS or 9.04 ( current version ) ;)

---

### Post by Sidewinder1 on 2009-08-08
Edgy is no longer supported. If possible, you may wish to consider upgrading to a newer version that is supported. Perhaps this link will help.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

HTH,
Side

---

### Post by Sidewinder1 on 2009-08-08
Cred beat me to it. ;-(

---

### Post by abhilashm86 on 2009-08-08
> **vivek shekar said:**
> Dear friends,

i am using ubunthu 7.04. now a days i am not able to donload any packegs i am geting errors like this....


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]Failed to fetch [url]http://in.archive.ubuntu.com/ubuntu

help me...

hi can i know reason still you are using 7.04?? use 8.04, hardy heron, they have told they'll support untill 2011.......

---

### Post by CatKiller on 2009-08-08
As credobyte says, Feisty (in this case) is no longer supported and the repositories have been moved. You can either upgrade to a new version that is still supported or edit sources.list with ```
sudo nano /etc/sources.list
``` to change all the instances of in.archive.ubuntu.com to old-releases.ubuntu.com to reflect the new location of the old repositories. You'll probably also want to decide which version you're using. You've got some edgy entries in there and some gutsy ones. Pick one of edgy, feisty or gutsy and use that consistently throughout.

---

