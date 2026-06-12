---
title: "Problem with Update Manager"
date: 2009-08-18
forum: General Help
---

### Post by thenailedone on 2009-08-18
Hi,

Since last night I get the following (or similar) errors when I try to update the package information for Update Manager:

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any specific reason for this?  Or do I need to do something to rectify this?


Cheers
Neil

EDIT:

Latest error:

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://ae.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2009-08-18
```
sudo apt-ge update && sudo apt-get upgrade
```

---

### Post by michy99 on 2009-08-18
Run this in terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
```

---

### Post by thenailedone on 2009-08-19
Thx for the replies... in the mean time I slapped on KDE 4.3 and now when I try and tell it to do a software update it gives me a window stating:

> Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-headers-generic
linux-image-2.6.28-15-generic
linux-image-generic

I ran both the commands given and it had no affect... :(

---

