---
title: "apt-get is broken"
date: 2009-10-09
forum: General Help
---

### Post by mulder_1 on 2009-10-09
While running apt-get update, I receive the following message.  I have tried removing partial, apt-get clean and so forth.  If bzip2 is installed, I get the same message except replace gzip with bzip2.  

I have replaces sources.list.  Everything resolves fine - packages actually do download with wget.


gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
  Sub-process gzip returned an error code (1)
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
99% [29 Sources gzip 0] [Connecting to ca.archive.ubuntu.com (91.189.88.31)]                                                                                                                       25.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
  Sub-process gzip returned an error code (1)
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
99% [30 Sources gzip 0]                                                                                                                                                                            25.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 521kB in 16s (31.1kB/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)
Reading package lists... Done

---

### Post by oldos2er on 2009-10-09
Dapper reached its end-of-life last July, so you might want to consider upgrading.

---

### Post by overdrank on 2009-10-09
To add to oldos2er you may look at [EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by mulder_1 on 2009-10-10
Perhaps - if I go that route I still need to get apt working...  I've seen many similar posts to this - it doesn't seem like there is an easy solution.

---

