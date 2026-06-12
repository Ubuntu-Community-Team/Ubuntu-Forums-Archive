---
title: "Size mismatch error on brand new install"
date: 2011-04-14
forum: General Help
---

### Post by byb3 on 2011-04-14
Hi,

I was playing with Debian for the first time and I have been trying to install postfix.

I type in
```
apt-get install postfix
```On that installation, and now also on a fresh Ubuntu 10.10 Server installation, I am also getting the exact same error:

```
root@netops1:/home/netops# apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ssl-cert
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb mail-reader openssl-blacklist
The following NEW packages will be installed
  postfix ssl-cert
0 upgraded, 2 newly installed, 0 to remove and 91 not upgraded.
Need to get 1,333kB of archives.
After this operation, 3,387kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick/main ssl-cert all 1.0.26 [14.5kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ maverick/main postfix i386 2.7.1-1 [1,318kB]
Fetched 16.1kB in 8s (1,829B/s)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.1-1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@netops1:/home/netops#
```I would like to do an apt-get update and then upgrade, but not even that works.

```
root@netops1:/home/netops# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  apparmor apparmor-utils bash-completion bind9-host bsdutils dhcp3-client dhcp3-common dnsutils dpkg fuse-utils ifupdown initscripts
  libapparmor-perl libapparmor1 libavahi-client3 libavahi-common-data libavahi-common3 libbind9-60 libblkid1 libc-bin libc6 libcairo2 libcups2
  libdbus-1-3 libdns66 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libfreetype6 libfuse2 libglib2.0-0 libgssapi-krb5-2 libisc60 libisccc60
  libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60 libpam-modules libpam-runtime libpam-smbpass libpam0g
  libparted0debian1 libplymouth2 libsqlite3-0 libssl0.9.8 libudev0 libuuid1 libwbclient0 libxml2 linux-firmware linux-headers-2.6.35-22
  linux-headers-2.6.35-22-generic-pae linux-image-2.6.35-22-generic-pae login mount openssh-client openssh-server openssl parted passwd plymouth
  plymouth-theme-ubuntu-text python python-apt python-minimal samba samba-common samba-common-bin samba-doc smbclient sudo sysv-rc sysvinit-utils
  tar tzdata udev update-inetd update-manager-core upstart util-linux uuid-runtime w3m winbind xkb-data
88 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 118MB of archives.
After this operation, 721kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main tzdata all 2011e-0ubuntu0.10.10 [683kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libpam0g i386 1.1.1-4ubuntu2 [91.7kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main dpkg i386 1.15.8.4ubuntu3.1 [2,073kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main mount i386 2.17.2-0ubuntu1.10.10.2 [174kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main tar i386 1.23-2ubuntu2 [403kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libc-bin i386 2.12.1-0ubuntu10.2 [739kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libc6 i386 2.12.1-0ubuntu10.2 [3,814kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main sysvinit-utils i386 2.87dsf-4ubuntu19 [110kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main sysv-rc all 2.87dsf-4ubuntu19 [79.5kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdbus-1-3 i386 1.4.0-0ubuntu1.2 [130kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libudev0 i386 162-2.2 [126kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libpam-modules i386 1.1.1-4ubuntu2 [323kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main python-minimal all 2.6.6-2ubuntu2 [35.7kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main passwd i386 1:4.1.4.2-1ubuntu3.2 [875kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main initscripts i386 2.87dsf-4ubuntu19 [73.9kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main python all 2.6.6-2ubuntu2 [172kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-image-2.6.35-22-generic-pae i386 2.6.35-22.35 [34.0MB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main ifupdown i386 0.6.10ubuntu3.1 [57.5kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main upstart i386 0.6.6-4 [190kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main util-linux i386 2.17.2-0ubuntu1.10.10.2 [527kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libssl0.9.8 i386 0.9.8o-1ubuntu4.4 [866kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main bsdutils i386 1:2.17.2-0ubuntu1.10.10.2 [80.3kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libuuid1 i386 2.17.2-0ubuntu1.10.10.2 [61.7kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libblkid1 i386 2.17.2-0ubuntu1.10.10.2 [111kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libsqlite3-0 i386 3.7.2-1ubuntu0.1 [381kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main xkb-data all 1.8-1ubuntu8.1~10.10.1 [440kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdrm2 i386 2.4.21-1ubuntu2.1 [30.7kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdrm-intel1 i386 2.4.21-1ubuntu2.1 [31.4kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdrm-nouveau1 i386 2.4.21-1ubuntu2.1 [21.4kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdrm-radeon1 i386 2.4.21-1ubuntu2.1 [22.2kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libpam-runtime all 1.1.1-4ubuntu2 [85.3kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main dhcp3-client i386 3.1.3-2ubuntu6.1 [256kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main dhcp3-common i386 3.1.3-2ubuntu6.1 [318kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main fuse-utils i386 2.8.4-1ubuntu1.3 [21.6kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main plymouth i386 0.8.2-2ubuntu5.1 [113kB]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libplymouth2 i386 0.8.2-2ubuntu5.1 [89.5kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libglib2.0-0 i386 2.26.1-0ubuntu1 [1,381kB]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libapparmor1 i386 2.5.1-0ubuntu0.10.10.4 [40.9kB]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libapparmor-perl i386 2.5.1-0ubuntu0.10.10.4 [42.5kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main bash-completion all 1:1.2-2ubuntu1.1 [140kB]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libfuse2 i386 2.8.4-1ubuntu1.3 [141kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main udev i386 162-2.2 [428kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libk5crypto3 i386 1.8.1+dfsg-5ubuntu0.6 [96.4kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libgssapi-krb5-2 i386 1.8.1+dfsg-5ubuntu0.6 [120kB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main apparmor i386 2.5.1-0ubuntu0.10.10.4 [358kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libkrb5-3 i386 1.8.1+dfsg-5ubuntu0.6 [349kB]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libkrb5support0 i386 1.8.1+dfsg-5ubuntu0.6 [42.7kB]
Get:49 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libxml2 i386 2.7.7.dfsg-4ubuntu0.1 [823kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main apparmor-utils i386 2.5.1-0ubuntu0.10.10.4 [110kB]
Get:51 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main dnsutils i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [151kB]
Get:52 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main bind9-host i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [66.3kB]
Get:53 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libisc60 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [157kB]
Get:54 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libdns66 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [654kB]
Get:55 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libisccc60 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [30.0kB]
Get:56 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libisccfg60 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [47.9kB]
Get:57 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main liblwres60 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [48.6kB]
Get:58 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libbind9-60 i386 1:9.7.1.dfsg.P2-2ubuntu0.2 [37.3kB]
Get:59 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libfreetype6 i386 2.4.2-2ubuntu0.1 [357kB]
Get:60 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libcairo2 i386 1.10.0-1ubuntu3 [921kB]
Get:61 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libldap-2.4-2 i386 2.4.23-0ubuntu3.5 [200kB]
Get:62 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libparted0debian1 i386 2.3-2ubuntu2 [229kB]
Get:63 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main openssh-server i386 1:5.5p1-4ubuntu5 [302kB]
Get:64 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main parted i386 2.3-2ubuntu2 [74.1kB]
Get:65 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main plymouth-theme-ubuntu-text i386 0.8.2-2ubuntu5.1 [20.5kB]
Get:66 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main python-apt i386 0.7.96.1ubuntu11.1 [200kB]
Get:67 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main update-manager-core i386 1:0.142.23 [197kB]
Get:68 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main uuid-runtime i386 2.17.2-0ubuntu1.10.10.2 [63.7kB]
Get:69 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libavahi-common-data i386 0.6.27-2ubuntu3.1 [35.0kB]
Get:70 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libavahi-common3 i386 0.6.27-2ubuntu3.1 [23.1kB]
Get:71 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libavahi-client3 i386 0.6.27-2ubuntu3.1 [54.3kB]
Get:72 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main openssh-client i386 1:5.5p1-4ubuntu5 [840kB]
Get:73 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libcups2 i386 1.4.4-6ubuntu2.3 [226kB]
Get:74 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main smbclient i386 2:3.5.4~dfsg-1ubuntu8.4 [13.6MB]
Get:75 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main update-inetd all 4.36ubuntu0.1 [20.3kB]
Get:76 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main w3m i386 0.5.2-6ubuntu1 [1,104kB]
Get:77 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libpam-smbpass i386 2:3.5.4~dfsg-1ubuntu8.4 [822kB]
Get:78 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main samba-common all 2:3.5.4~dfsg-1ubuntu8.4 [395kB]
Get:79 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main libwbclient0 i386 2:3.5.4~dfsg-1ubuntu8.4 [128kB]
Get:80 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-firmware all 1.38.5 [12.7MB]
Get:81 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-22 all 2.6.35-22.35 [10.3MB]
Get:82 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-22-generic-pae i386 2.6.35-22.35 [776kB]
Get:83 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main samba-common-bin i386 2:3.5.4~dfsg-1ubuntu8.4 [5,754kB]
Get:84 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main samba i386 2:3.5.4~dfsg-1ubuntu8.4 [7,454kB]
Get:85 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main winbind i386 2:3.5.4~dfsg-1ubuntu8.4 [5,206kB]
Get:86 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main openssl i386 0.9.8o-1ubuntu4.4 [400kB]
Get:87 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main samba-doc all 2:3.5.4~dfsg-1ubuntu8.4 [1,742kB]
Get:88 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main sudo i386 1.7.2p7-1ubuntu2.1 [315kB]
Fetched 82.0MB in 7min 24s (185kB/s)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.8.4ubuntu3.1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.1.4.2-1ubuntu3.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.17.2-0ubuntu1.10.10.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.23-2ubuntu2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.12.1-0ubuntu10.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu10.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu19_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu19_all.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/shadow/passwd_4.1.4.2-1ubuntu3.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu19_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.10ubuntu3.1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.6.6-4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.17.2-0ubuntu1.10.10.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.17.2-0ubuntu1.10.10.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2_all.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu6.1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu6.1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.26.1-0ubuntu1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.8.4-1ubuntu1.3_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.2_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.10.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.10.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_5.5p1-4ubuntu5_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.2-6ubuntu1_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.5.4~dfsg-1ubuntu8.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.5.4~dfsg-1ubuntu8.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.5.4~dfsg-1ubuntu8.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.4_i386.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-doc_3.5.4~dfsg-1ubuntu8.4_all.deb  Size mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p7-1ubuntu2.1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```Why onearth is this happening, I've never had issues before?

---

### Post by yaplej on 2011-06-09
I am having the same type of problems with a new install of ubuntu10.04.2 server i386.  I first thought it was because I am behind a proxy.  Is that the case for you also?

---

### Post by byb3 on 2011-09-01
Hi,

Just for other people who may find this post, I was behind a proxy.

However I was not aware that the proxy I was using was doing some extensive caching.  We have two proxies where we work, one is live and one does a lot of caching.  I was unknowingly using the caching one and as soon as I changed my problems disappeared.

Regards,

---

