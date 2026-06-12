---
title: "Need help with ncftp using Kubuntu linux"
date: 2006-03-18
forum: General Help
---

### Post by bushnerd on 2006-03-18
when I type the command:


apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev 


(guide I am using is at:[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3) )

I get the error: "E: Couldn't find package ncftp"

I seached google, but all I got was SUSE 9.3 problems.

Any idea what I am doing wrong??

I am using Kubuntu 5.10

Thanks for your time!

---

### Post by adamkane on 2006-03-18
Looks like ncftp is only available to Dapper via the Universe repository:
[http://packages.ubuntulinux.org/dapper/net/ncftp](http://packages.ubuntulinux.org/dapper/net/ncftp)

---

