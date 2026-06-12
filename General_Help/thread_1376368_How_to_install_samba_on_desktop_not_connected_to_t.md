---
title: "How to install samba on desktop not connected to the internet"
date: 2010-01-09
forum: General Help
---

### Post by ibrahim.k on 2010-01-09
Hi,
I have a desktop with ultimate edition installed on it (ubuntu 9.4)
how can I install samba file sharing on it ??
on the desktop I dont have internet connection !

Thnx in advance

---

### Post by zey on 2010-01-09
then you must have the samba package
and then install it.
you can get it from CD or download from internet.

[z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by ibrahim.k on 2010-01-09
It didnt work !
Error: Dependency is not satisfiable: samba 
(=3.0.22-1ubuntu3.9) 


> **zey said:**
> then you must have the samba package
and then install it.
you can get it from CD or download from internet.

[z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by SecretCode on 2010-01-09
These are the dependencies for package samba:
```
$ sudo aptitude show samba
Package: samba
New: yes
State: not installed
Version: 2:3.4.0-3ubuntu5.1
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 18.3M
Depends: samba-common (= 2:3.4.0-3ubuntu5.1), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1), libc6 (>= 2.8), libcap2 (>= 2.10),
         libcomerr2 (>= 1.01), libcups2 (>= 1.4.0), libgnutls26 (>= 2.7.14-0), libgssapi-krb5-2 (>= 1.7dfsg~beta1), libk5crypto3 (>=
         1.6.dfsg.2), libkrb5-3 (>= 1.7dfsg~alpha1), libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpopt0 (>= 1.14),
         libtalloc1 (>= 1.4.0~git20090718), libwbclient0 (>= 2:3.4.0~pre2), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0,
         libpam-runtime (>= 0.76-13.1), libpam-modules, lsb-base (>= 3.2-13), procps, update-inetd, adduser
```

You will need to have all of them installed as well ... and I'm not sure how to do it easily; you might have to check each one and copy it over and install it separately.

---

### Post by mk1w86 on 2010-01-09
Take a look at this guide:

[https://help.ubuntu.com/community/AptGet/Offline/PrintUris](https://help.ubuntu.com/community/AptGet/Offline/PrintUris)

Here is how to do the same thing in Synaptic:

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by mac9416 on 2010-01-09
Or download the packages with [Keryx]("http://keryxproject.org").

---

### Post by normanp on 2010-01-25
I have just succeeded using this method in jaunty 9.04:

Download the 7 files below from the Internet where access is possible, the upper 6 files from:
[http://archive.ubuntu.com/ubuntu/dists/jaunty/](http://archive.ubuntu.com/ubuntu/dists/jaunty/)
and the last samba file from:
[https://launchpad.net/ubuntu/+archive/primary/+sourcepub/535715/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/535715/+listing-archive-extra)

On the Ubuntu machine, assuming you are logged on as user 'myuser' create this file structure in /home/myuser/UbuntuRepositories/repository/
```

  |
  |_dists
  |    |_ jaunty
  |        |_____ main
  |        |        |_____binary-i386
  |        |                   |________Packages.bz2
  |        |                            Packages.gz
  |        |                            Release.txt
  |        |_____Contents-i386.gz
  |              Release.gpg
  |              Release.txt
  |
  |_pool
       |_main
           |_s
              |_samba
                   |_____samba_3.3.2-1ubuntu3_i386.deb


```
Now run Synaptic Package Manager:
Settings, Repositories
Turn off all Downloadable and CD-Rom
Go to Third Party Software tab
Click +Add
type:
deb file:///home/myuser/UbuntuRepositories/repository jaunty main
+Add Source
Ensure this item ticked, Close
(if you go back & edit you will see URI of file:///home/myadmin/UbuntuRepositories/repository and Dist as jaunty, and Components as main)

Reload

Find 'samba' in the list of packages & check it.
Apply

You can now share folders.
I have not checked the security implications - but clearly one should be cautious of allowing write access...

I hope this helps.

This was helpful:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
The 'pool' directory part & the samba file were discovered when the package Manager failed without it - the file found with a Google search.

---

