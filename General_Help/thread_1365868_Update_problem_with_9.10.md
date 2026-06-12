---
title: "Update problem with 9.10"
date: 2009-12-27
forum: General Help
---

### Post by Janeleaper on 2009-12-27
Since upgrading to 9.10 my system is not updating automatically.  I have an orange triangle on my top panel which, right clicked, says 

"the update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting "check for updates" and check if some of the listed repositories fail.

When I do a check I get the message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://people.ubuntu.com/~doko/ubuntu/gutsy/Packages.gz](http://people.ubuntu.com/~doko/ubuntu/gutsy/Packages.gz)  404  Not Found
Failed to fetch [http://people.ubuntu.com/~doko/ubuntu/gutsy/Sources.gz](http://people.ubuntu.com/~doko/ubuntu/gutsy/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I've tried changing Software Sources several times without making any difference.

I think I've seen a thread on this topic by someone else, but I can't find it now.

---

### Post by howefield on 2009-12-27
The Gutsy repositories went end of life sometime ago.

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

### Post by Janeleaper on 2009-12-27
OK.  But my updater is still refusing to update automatically and thinks there is a problem.  Do you know how I fix it?

---

### Post by howefield on 2009-12-27
I never upgrade, only clean install so haven't had this issue but if I did, I'd probably backup the sources.list, then delete it and then rebuild a new one using System > Administration > Software Sources.

Finish off with update/reload.

Does this make sense, or do you need help to do it ?

---

### Post by bjk03 on 2009-12-27
> **Janeleaper said:**
> OK.  But my updater is still refusing to update automatically and thinks there is a problem.  Do you know how I fix it?

The following link will tell you how to remove repositories. [https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories")

---

### Post by Janeleaper on 2009-12-27
I have removed all the repositories that mention gutsy, and I restarted the computer, but I'm still getting the same message.

---

### Post by Janeleaper on 2009-12-27
It's OK.  I had to remove the gutsy cd as well, even though it was unchecked.  Update manager seems to be working fine now.  Thanks to all for the assistance.

---

