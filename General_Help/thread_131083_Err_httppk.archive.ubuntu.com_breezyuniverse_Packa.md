---
title: "Err http://pk.archive.ubuntu.com breezy/universe Packages"
date: 2006-02-15
forum: General Help
---

### Post by shams2 on 2006-02-15
hi,
apt-get was working fine, but suddenly today got this error with  the apt-get update:
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy-backports/multiverse Packages
Get:7 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [7 Packages gzip 0]                                             26.9kB/s 0s
gzip: stdin: not in gzip format
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 7B in 10s (1B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead
i run the apt-get clean all and then apt-get update and got the same error, help me please?

---

### Post by deBaas on 2006-02-15
```

# apt-get update
# apt-get upgrade

```
should do the trick. Otherwise try a different mirror.

---

