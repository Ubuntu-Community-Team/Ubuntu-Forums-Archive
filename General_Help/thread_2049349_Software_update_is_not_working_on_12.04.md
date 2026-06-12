---
title: "Software update is not working on 12.04"
date: 2012-08-28
forum: General Help
---

### Post by bongobuntian on 2012-08-28
Hi There,

I tried to update from update manager and also from terminal using sudo apt-get update.

But all the time its showing some kind of errors and not updating properly. As for example, its showing: 

> bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.and 

> W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.these errors when I tried from apt-get update. Any idea how to fix these?

Software manager showing its 13days since the package information was last updated.

Any kind of help will be appreciated.

---

### Post by bongobuntian on 2012-08-28
Just tried from update manager and got this error

> W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Gokutux on 2012-08-28
Try to change server from update manager->settings and choose main server... and then update your system!

---

### Post by bongobuntian on 2012-08-28
> **Gokutux said:**
> Try to change server from update manager->settings and choose main server... and then update your system!

Its already selected :(

---

### Post by Gokutux on 2012-08-28
Uncheck partner sources and try again...

---

### Post by bongobuntian on 2012-08-28
> **Gokutux said:**
> Uncheck partner sources and try again...

that worked, but what about the software updates that I installed from the partner sources?

---

### Post by Gokutux on 2012-08-28
> **bongobuntian said:**
> that worked, but what about the software updates that I installed from the partner sources?

By default there are 2 partner sources,Canonical partners and Canonical partners(source-code)... Your problem is with the second. try to insert the source manual without eraze the default,you will see the informations that needed if you select the second source and press edit. Then check the source you create anad try to update...

---

