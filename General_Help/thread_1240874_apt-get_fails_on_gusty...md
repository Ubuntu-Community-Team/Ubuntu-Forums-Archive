---
title: "apt-get fails on gusty.."
date: 2009-08-15
forum: General Help
---

### Post by cjjoy1980 on 2009-08-15
On gust I am no longer able to install packages, I am getting the following error

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]


Came to know that we gusty repository is no longer in use.  

Can I only update my /etc/apt/sources.list to point to Hardy or should upgrade my system completly to hardy 

In either case please let me know how to do it.

-Joy

---

### Post by Soul-Sing on 2009-08-15
updatemanager doesn't come with an upgrade option?

---

### Post by andru183 on 2009-08-15
k, if you follow the link you get a 404 so maybe thats the reason this is failing, have you tried installing anything else or using sudo aptitude? ive nevery used or come in contact with gusty so i dont know if this command can be used so forgive my inexp

---

### Post by cjjoy1980 on 2009-08-15
update-manager throws the same error:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

---

### Post by arpanaut on 2009-08-15
This may help...

[http://ubuntuforums.org/showthread.php?t=1236321&highlight=EOL+gutsy](http://ubuntuforums.org/showthread.php?t=1236321&highlight=EOL+gutsy)

---

### Post by lswb on 2009-08-15
As I understand it, support for Gutsy has ended. LTS releases are supported for 3 years Desktop/5 yrs server but other releases are only supported for 18 months. Probably best to upgrade to hardy. Highly recommended to backup anything important first. While most upgrades work OK there are always some people who report serious problems sometimes including data loss after an upgrade.

---

